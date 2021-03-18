---
title: "Todos e Fixmes"
date: 2021-03-18T10:17:41-03:00
draft: false
---

Pesquisa palavras `TODO` e `FIXME`  a partir do diretório que o vim foi aberto, ignorando pastas e arquivos do ``wildignore``.

```vim
set wildignore=.git,.git/**
set wildignore+=.svn,.svn/**
set wildignore+=node_modules,node_modules/**
set wildignore+=.venv
set wildignore+=dist,dist/**
set wildignore+=target,target/**
set wildignore+=build,build/**
set wildignore+=vendor,vendor/**
set wildignore+=ios,ios/**
set wildignore+=android,android/**
set wildignore+=_site,_site/**
set wildignore+=*/coverage,*/coverage/**
set wildignore+=*/_reports,*/_reports/**
set wildignore+=DS_Store,DS_Store/**
set wildignore+=tags

function! Tasks()
    vimgrep /\C\<TODO\>\|\C\<FIXME\>/j **
    copen
endfunction
