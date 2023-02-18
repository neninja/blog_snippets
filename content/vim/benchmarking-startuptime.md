---
title: "Testar tempo de inicialização"
date: 2023-02-17T17:40:15-03:00
draft: false
summary: "Útil para benchmarking de config/plugins"
---

Inicie com `--startuptime`

```bash
nvim --startuptime startup.log -c exit && tail -5 startup.log
```

Com o exemplo de output abaixo, o tempo de inicialização é `006.928 ms`

```txt
003.790  000.790  000.141: require('vim._init_packages')
003.797  001.215: init lua interpreter
005.248  001.451: expanding arguments
005.408  000.160: inits 2
006.928  001.521: init highlight
```
