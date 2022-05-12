# 나의 vim 

youcompleteme 의 python3.6 error를 해결하기 위해서 `brew install macvim` 을 설치해주자.

# .vimrc

```
set nocompatible              " required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'ambv/black'
Plugin 'vim-syntastic/syntastic'
Plugin 'nvie/vim-flake8'
Plugin 'jnurmine/Zenburn'
Plugin 'scrooloose/nerdtree'
Plugin 'jistr/vim-nerdtree-tabs'
Plugin 'kien/ctrlp.vim'
Plugin 'tpope/vim-fugitive'
Plugin 'Lokaltog/powerline', {'rtp': 'powerline/bindings/vim/'}
Plugin 'gmarik/Vundle.vim'
" Plugin 'tpope/vim-fugitive'
Plugin 'git://git.wincent.com/command-t.git'
Plugin 'file:///home/gmarik/path/to/plugin'
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
Plugin 'tmhedberg/SimpylFold'
Plugin 'Valloric/YouCompleteMe'
Plugin 'prettier/vim-prettier', { 'do': 'yarn install' }


" add all your plugins here (note older versions of Vundle
" used Bundle instead of Plugin)

" ...

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required

set nu
set foldmethod=indent
set foldlevel=99
set encoding=utf-8
set backspace=indent,eol,start
set hlsearch


colorscheme zenburn

let g:SimpyFold_docstring_preview=0
let g:ycm_autoclose_preview_window_after_completion=1
let python_highlight_all=1
let NERDTreeIgnore=['\.pyc$', '\~$'] "ignore files in NERDTree
let g:black_virtualenv='~/.vim/black'

autocmd BufWritePre *.py execute ':Black'
" autocmd BufWritePre *.js,*.jsx,*.mjs,*.ts,*.tsx,*.css,*.less,*.scss,*.json,*.graphql,*.md,*.vue,*.yaml,*.html execute ':Prettier'

syntax on

map <leader>g  :YcmCompleter GoToDefinitionElseDeclaration<CR>


:au BufNewFile,BufRead *.py
    \ set tabstop=4 |
    \ set softtabstop=4 |
    \ set shiftwidth=4 |
    \ set textwidth=79 |
    \ set expandtab |
    \ set autoindent |
    \ set fileformat=unix

au BufNewFile,BufRead *.js, *.html, *.css
    \ set tabstop=2 |
    \ set softtabstop=2 |
    \ set shiftwidth=2




```

이후에 
```
cd ~/.vim/bundle/YouCompleteMe
python install.py
```
해줘야 YouCompleteMe를 사용할 수 있다.
그런데 이때 (macbook) xcode 가 설치되어 있지 않다면 python headers 를 찾지 못했다고 error를 띄운다. 
따라서 xcode를 설치해줘야 한다.
