+++
draft = true
date = 2021-02-01T03:06:38-03:00
title = "[Polybar] Feriados en Argentina"
description = "Modulo de Feriados en Argentina para Polybar"
slug = ""
authors = ["gabox"]
tags = ["polybar", "linux", "feriado", "python"]
categories = ["scripts"]
externalLink = ""
series = []
+++

La idea es tener un módulo en `Polybar` que muestre información del próximo feriado en Argentina y se vea algo así:

![modulo-feriado](/img/module-feriado.png)

## Requisitos
- [Polybar](https://polybar.github.io/) 🙃.
- Script [feriados](https://github.com/centaurialpha/feriado-polybar) ™️.
- [Dunst](https://dunst-project.org/) (opcional).

Hace un tiempo escribí un script en Python que muestra el próximo feriado
usando la [API pública de Feriados Argentinos](https://pjnovas.gitbooks.io/no-laborables/content/). La salida del script es algo así:

```
$ ./feriados
Próximo feriado: 15 Feb
Motivo: Carnaval
Tipo: inamovible
Más información: https://es.wikipedia.org/wiki/Carnaval
```

```ini
[module/feriados]
type = custom/script
exec = $HOME/.scripts/feriados -f
format = <label>
format-prefix = " "
format-prefix-foreground = ${color.teal}
format-padding = 1
interval = 43200
click-left = $HOME/.scripts/feriados -i
click-right = dunstify $($HOME/.scripts/feriados -m)
```
