# clion-config
Configuration for CLion C++ development for CPSC 5005 (2023)

## [CheatSheet](https://resources.jetbrains.com/storage/products/clion/docs/CLion_ReferenceCard.pdf)

- `CTRL-Alt-l` - run code formatter
- `CTRL-Alt-s` - Open ssh session
- `Alt-F12` - open/close Terminal
- `CTRL-Alt-A` - find possible actions
- `Alt-Insert` - run automatic code generation (create new class from file explorer, create methods from code editor)

## Auto Formating

I've included formatting adjustments from the CLion default code formating.
- `Default.xml`
  - agnostic to conditionals and loop brackets.
  - sets char limit to 80 for typing

By default the command to re-format the code file is: `CTRL-Alt-l` or `CTRL-Alt-Shift-L` (whole project)

Upload from `Settings > Editor > Code Style > Scheme` click the ⚙ > `import scheme` and select the `.xml` file.

adjust as needed!

## File Headers

This will automatically include the file header information into new C++ files. 
This will not automatically adjust any existing files.

Navigate to `Settings > Editor > File and Code Templates` then go to the `Includes` tab.
Copy the following into the C File Header Template:

```
#if ($HEADER_COMMENTS)
//
//  $USER_NAME
//  ${FILE_NAME}
//  ${DATE}
//  Purpose: TODO -- add description
//
#end
```

## IdeaVim Plugin

I started using the [IdeaVim](https://github.com/JetBrains/ideavim) plugin.
If you are used to Vim/Vim motions I've included my `.ideavimrc`.

https://danielmiessler.com/p/vim/
https://vim-adventures.com/

Install/Enable the plugin and copy `.ideavimrc` into your home directory.
 - osx/linux `~/.ideavimrc`
 - windows `C:/Users/[myname]/.ideavimrc`

CLion will require a re-start in order to apply the settings

example `.ideavimrc`:
```
set tabstop=4 softtabstop=4
set shiftwidth=4
set expandtab
set exrc
set nu
set hidden
set noerrorbells
set noswapfile
set nobackup
set incsearch
set scrolloff=15
set signcolumn=yes
set colorcolumn=80
set termguicolors
set cmdheight=2
set relativenumber
set updatetime=50
set shortmess+=c

let mapleader=" "
xnoremap <leader>p _dp
vnoremap <leader>p _dp

vnoremap <leader>y "*y
nnoremap <leader>p "*p
vnoremap <C-c> "*y
nnoremap <C-v> "*p
nnoremap <leader>w :w!<cr>
nnoremap <C-s> :w!<cr>
inoremap <C-c> <esc>
nnoremap <leader>f :action ReformatCode<CR>

#Code Generation
nnoremap <leader>gc :action GenerateConstructor<CR>
nnoremap <leader>gg :action GenerateGetterandSetter<CR>
nnoremap <leader>go :action OverrideMethods<CR>
nnoremap <leader>gd :action CodeCompletion<CR>

nmap gb <Action>(Back)
nmap gD <Action>(GotoTypeDeclaration)
nmap gf <Action>(Forward)
nmap gl <Action>(QuickJavaDoc)
nmap gL <Action>(QuickImplementations)
nmap gy <Action>(ShowErrorDescription)

Plug 'tpope/vim-commentary'		    # [count]gc{motion}, o_gc, v_gc, gcc
```

## TODO

- [ ] Automagic function documentation (non Doxygen format), I assume this goes into Settings > Editor > Code, but need some custom includes for post function body?
```
type methodIdentifier(type parameterIdentfier, …);
// description of purpose
// pre(conditions): state anything that must be true for the method to work properly
// post(conditions): state changes that affect class members
```
- [ ]  Screen shots for setup instructions
- [ ]  Additional Plug-in explorations

