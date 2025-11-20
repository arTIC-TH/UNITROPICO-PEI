---
title: "Scraping de données d'entreprises"
format: html
editor: visual
---


https://companydata.com/companies/ireland/car-dealers/#:~:text=Number%20of%20Car%20dealers%20in,dealers%20in%20Ireland%20is%202%2C700.


```{r}
#| message: FALSE
#| warning: FALSE

# Packages nécessaires
library(rvest)
library(httr)
library(dplyr)
library(purrr)
library(readr)

# ===============================
# CONFIGURATION
# ===============================

# URL de base à ADAPTER
base_url <- "https://example.com/companies/ireland/car-dealers?page="

# Nombre de pages à parcourir (à adapter)
n_pages <- 5

# User-Agent pour éviter d’être bloqué
ua <- httr::user_agent("Mozilla/5.0 (Windows NT 10.0; Win64; x64)")

# ===============================
# FONCTION POUR SCRAPER UNE PAGE
# ===============================

scrape_page <- function(page_number) {

  url <- paste0(base_url, page_number)
  message("Scraping: ", url)

  # Charger la page
  page <- httr::GET(url, ua)
  html <- read_html(page)

  # EXTRAIRE LES ÉLÉMENTS (À ADAPTER)
  cards <- html %>% html_elements(".company-card")

  data <- tibble(
    name = cards %>% html_element(".company-name") %>% html_text(trim = TRUE),
    address = cards %>% html_element(".company-address") %>% html_text(trim = TRUE),
    phone = cards %>% html_element(".company-phone") %>% html_text(trim = TRUE),
    website = cards %>% html_element("a.company-website") %>% html_attr("href")
  )

  return(data)
}

# ===============================
# SCRAPER TOUTES LES PAGES
# ===============================

all_data <- map_dfr(1:n_pages, scrape_page)

# Aperçu
head(all_data)

# ===============================
# EXPORT CSV
# ===============================

write_csv(all_data, "car_dealers.csv")

message("Fichier exporté : car_dealers.csv")

