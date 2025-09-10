---
title: "Reuniones PEI - Miércoles y Socialización"
format:
  html: default
  docx: default
  pdf: default
  pptx: default
execute:
  echo: false
---

# Calendario de reuniones PEI  
_Período: 13 de mayo – 10 de septiembre de 2025_  
_Días: miércoles + socialización (fechas especiales)

```{r}
#| label: reuniones-pei
#| message: false
#| warning: false

library(knitr)

reuniones <- data.frame(
  Nº = 1:22,
  Fecha = c(
    "Miércoles 14 de mayo de 2025",
    "Miércoles 21 de mayo de 2025",
    "Miércoles 28 de mayo de 2025",
    "Miércoles 4 de junio de 2025",
    "Martes 10 de junio de 2025 (Socialización)",
    "Miércoles 11 de junio de 2025 (Socialización)",
    "Jueves 12 de junio de 2025 (Socialización)",
    "Miércoles 18 de junio de 2025",
    "Miércoles 25 de junio de 2025",
    "Miércoles 2 de julio de 2025",
    "Miércoles 9 de julio de 2025",
    "Miércoles 16 de julio de 2025",
    "Miércoles 23 de julio de 2025",
    "Miércoles 30 de julio de 2025",
    "Miércoles 6 de agosto de 2025",
    "Martes 12 de agosto de 2025 (Socialización)",
    "Miércoles 13 de agosto de 2025",
    "Miércoles 20 de agosto de 2025",
    "Viernes 29 de agosto de 2025 (Socialización)",
    "Miércoles 27 de agosto de 2025",
    "Miércoles 3 de septiembre de 2025",
    "Miércoles 10 de septiembre de 2025"
  ),
  Tema = "",
  Observaciones = "",
  Evidencia = ""
)

kable(reuniones, caption = "Lista de reuniones programadas del PEI")
