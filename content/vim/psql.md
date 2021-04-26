---
title: "Queries postgresql"
date: 2021-04-26T09:01:15-03:00
draft: false
summary: "Executa queries por ocmando"
---

Realiza execução de queries com `:Psql <query>`, como `:Psql select * from users where nickname = 'Neni'`.

- No vimrc:

```vim
" vimrc

execute 'source ~/.vimrc-local'

function! s:PsqlComplete(A, L, P) abort
    let commands = [ 
                \ "SELECT ",
                \ "SELECT * ",
                \ "TOP ",
                \ "FROM ",
                \ "WHERE ",
                \ "LIMIT ",
                \]
    return filter(commands, 'v:val =~ "^" . a:A')
endfunction

" THANKS: https://github.com/tpope/vim-dadbod
" Psql select * from table where name = 'nome'
command! -nargs=+ -complete=customlist,s:PsqlComplete Psql exe 'RunCmd psql -w --dbname postgresql://'.g:dbs_psql[g:db_psql]["url"].' -c "'.<q-args>.'"'
command! -nargs=1 -complete=customlist,g:PsqlCompleteTable PsqlSelectAllFrom exe 'Psql select * from '.<q-args>
command! PsqlSelectAllTables Psql SELECT table_name FROM information_schema.tables WHERE table_schema = 'public' ORDER BY table_name
```

- Em outro arquivo importado mas não versionado:

```vim
" vimrc-local

"let g:dbs_psql = [
"  \ { 'name': 'name_connection', 'url': '[<user>[:<password>]@][<host>[:<port>]]/[<database>]' },
"  \ { 'name': 'db_dev', 'url': 'username:password@localhost:5432/database' },
"  \ { 'name': 'db_prod', 'url': 'username:password@localhost:5432/database' },
"  \ ]
" let g:db_psql = 'name_conection'

" function! g:PsqlCompleteTable(A, L, P) abort
"     let commands = [ 
"                 \ "users",
"                 \]
"     return filter(commands, 'v:val =~ "^" . a:A')
" endfunction
```
