---
title: "Repetição de comandos terminal"
date: 2023-02-15T10:35:15-03:00
draft: false
summary: "Reexecução de comandos com enter"
---

Diversas vezes preciso ficar repetindo um comando, seja algum tipo de ping ou teste. Ao invés de usar <kbd>⬆</kbd><kbd>enter</kbd> é possível utilizar somente <kbd>enter</kbd> com:

```sh
while $@; read line; do true; done;
```

Caso seja algo repetitivo, recomendo a criação de uma função no seu `~/.bashrc`

```sh
# wrl echo "a"
wrl(){
  while $@; read line; do true; done;
}
```
