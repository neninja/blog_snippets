---
title: "Quickfix: Macro"
date: 2023-02-14T23:07:15-03:00
draft: false
summary: "Macro por item"
---

Simule uma macro por item de uma `quickfix list` com `:cdo normal!........`. Para renomear uma propriedade por exemplo:

```vim
:cdo exe "normal!ceNovoNomeDoEnum" | update
```
