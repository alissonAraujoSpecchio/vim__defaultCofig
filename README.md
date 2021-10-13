# vim__defaultCofig
My default configuration for vim

Paste it on ~/.vimrc file:
```
set tabstop=4
set shiftwidth=4
set softtabstop=4
set expandtab
set smarttab
set smartindent

" The '#' after the '==' is for case-sensitive
function! Build()
    :w
    if &filetype ==# 'javascript' || &filetype ==# 'json' || &filetype ==# 'css'
        :!moduli build
    elseif &filetype ==# 'html'
        :!google-chrome %
    elseif &filetype ==# 'python'
        :!python %
    "elseif &filetype ==# 'adoc'
    "    :!echo teste
    "    :!asciidoctor %
    "elseif &filetype ==# 'txt'
    "    :!echo txt
    endif
endfunction

function! FoldMethodManual()
    set foldmethod=manual
    echo "fold mode: manual"
endfunction

function! FoldMethodIndent()
    set foldmethod=indent
    echo "fold mode: indent"
endfunction

" Function used to format and show an unformated JSON
function! JsonView()
    :%s/\n//g
    :w 
    u
    :!cat % | jq
    :w
endfunction

nnoremap <S-F5> :call Build()<CR>
nnoremap <F6> :call FoldMethodIndent()<CR>
nnoremap <F7> :call FoldMethodManual()<CR>
```
