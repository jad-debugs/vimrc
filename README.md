# Algorithm-DataStructures

Implementations of common algorithms and data structures used for competitive programming.

## Vim plugin

The algorithms and data structures can easily be pasted into a document using the included Vim plugin.

![demonstration](demonstration.gif)

### Installation

Use [vim-plug](https://github.com/junegunn/vim-plug) or any Vim plugin manager of your choice.
The plugin [fzf](https://github.com/junegunn/fzf) is a requirement.

With vim-plug:

```vim
Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }
Plug 'jakobkogler/Algorithm-DataStructures'
```

### Command/Usage

The plugin defines a single command `AlgDS`.
It can be mapped like this:

```vim
nmap <leader>alg :AlgDS<CR>
```

## Pretty Printer

There are some pretty printer for GDB.
You can activate them by putting the following in your `~/.gdbinit`:

```sh
source ~/.vim/plugged/Algorithm-DataStructures/prettyprint.py
```

## License

WTFPL

<p align="center">
  <a href="https://www.vim.org/scripts/script.php?script_id=5779">
    <img alt="Coc Logo" src="https://user-images.githubusercontent.com/251450/55009068-f4ed2780-501c-11e9-9a3b-cf3aa6ab9272.png" height="160" />
  </a>
  <p align="center">Make your Vim/Neovim as smart as VSCode.</p>
  <p align="center">
    <a href="/LICENSE.md"><img alt="Software License" src="https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square"></a>
    <a href="https://github.com/neoclide/coc.nvim/actions"><img alt="Actions" src="https://img.shields.io/github/workflow/status/neoclide/coc.nvim/coc.nvim%20CI?style=flat-square"></a>
    <a href="/doc/coc.txt"><img alt="Doc" src="https://img.shields.io/badge/doc-%3Ah%20coc.txt-brightgreen.svg?style=flat-square"></a>
    <a href="https://gitter.im/neoclide/coc.nvim"><img alt="Gitter" src="https://img.shields.io/gitter/room/neoclide/coc.nvim.svg?style=flat-square"></a>
  </p>
</p>

---

<img alt="Gif" src="https://user-images.githubusercontent.com/251450/55285193-400a9000-53b9-11e9-8cff-ffe4983c5947.gif" width="60%" />

_True snippet and additional text editing support_

<a href="https://www.zhipin.com/job_detail/b872ed13edf92a701nZz2967ElFW.html" target="_blank"><img src="https://alfs.chigua.cn/dianyou/data/platform/default/20210322/react.jpg"></a>

## Why?

- 🚀 **Fast**: [instant increment completion](https://github.com/neoclide/coc.nvim/wiki/Completion-with-sources), increment buffer sync using buffer update events.
- 💎 **Reliable**: typed language, tested with CI.
- 🌟 **Featured**: [full LSP support](https://github.com/neoclide/coc.nvim/wiki/Language-servers#supported-features)
- ❤️ **Flexible**: [configured like VSCode](https://github.com/neoclide/coc.nvim/wiki/Using-the-configuration-file), [extensions work like in VSCode](https://github.com/neoclide/coc.nvim/wiki/Using-coc-extensions)

## Quick Start

Install [nodejs](https://nodejs.org/en/download/) >= 10.12:

```sh
curl -sL install-node.now.sh/lts | bash
```

For [vim-plug](https://github.com/junegunn/vim-plug) users:

```vim
" Use release branch (recommend)
Plug 'neoclide/coc.nvim', {'branch': 'release'}

" Or build from source code by using yarn: https://yarnpkg.com
Plug 'neoclide/coc.nvim', {'branch': 'master', 'do': 'yarn install --frozen-lockfile'}
```

in your `.vimrc` or `init.vim`, then restart Vim and run `:PlugInstall`.

Checkout [Install
coc.nvim](https://github.com/neoclide/coc.nvim/wiki/Install-coc.nvim) for
more info.

You **have to** install coc extension or configure language servers for
LSP support.

Install extensions like:

    :CocInstall coc-json coc-tsserver

Or configure language server in `coc-settings.json` opened by
`:CocConfig`, like:

```json
{
  "languageserver": {
    "go": {
      "command": "gopls",
      "rootPatterns": ["go.mod"],
      "trace.server": "verbose",
      "filetypes": ["go"]
    }
  }
}
```

Checkout wiki for more details:

- [Completion with sources](https://github.com/neoclide/coc.nvim/wiki/Completion-with-sources)
- [Using the configuration file](https://github.com/neoclide/coc.nvim/wiki/Using-the-configuration-file)
- [Using coc extensions](https://github.com/neoclide/coc.nvim/wiki/Using-coc-extensions)
- [Configure language servers](https://github.com/neoclide/coc.nvim/wiki/Language-servers)
- [F.A.Q](https://github.com/neoclide/coc.nvim/wiki/F.A.Q)

Checkout `:h coc-nvim` for vim interface.

## Example vim configuration

Configuration is required to make coc.nvim easier to work with, since it
doesn't change your key-mappings or Vim options. This is done as much as
possible to avoid conflict with your other plugins.

**❗️Important**: Some Vim plugins could change key mappings. Please use
`:verbose imap <tab>` to make sure that your keymap has taken effect.

```vim
" Set internal encoding of vim, not needed on neovim, since coc.nvim using some
" unicode characters in the file autoload/float.vim
set encoding=utf-8

" TextEdit might fail if hidden is not set.
set hidden

" Some servers have issues with backup files, see #649.
set nobackup
set nowritebackup

" Give more space for displaying messages.
set cmdheight=2

" Having longer updatetime (default is 4000 ms = 4 s) leads to noticeable
" delays and poor user experience.
set updatetime=300

" Don't pass messages to |ins-completion-menu|.
set shortmess+=c

" Always show the signcolumn, otherwise it would shift the text each time
" diagnostics appear/become resolved.
if has("patch-8.1.1564")
  " Recently vim can merge signcolumn and number column into one
  set signcolumn=number
else
  set signcolumn=yes
endif

" Use tab for trigger completion with characters ahead and navigate.
" NOTE: Use command ':verbose imap <tab>' to make sure tab is not mapped by
" other plugin before putting this into your config.
inoremap <silent><expr> <TAB>
      \ pumvisible() ? "\<C-n>" :
      \ <SID>check_back_space() ? "\<TAB>" :
      \ coc#refresh()
inoremap <expr><S-TAB> pumvisible() ? "\<C-p>" : "\<C-h>"

function! s:check_back_space() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction

" Use <c-space> to trigger completion.
if has('nvim')
  inoremap <silent><expr> <c-space> coc#refresh()
else
  inoremap <silent><expr> <c-@> coc#refresh()
endif

" Make <CR> auto-select the first completion item and notify coc.nvim to
" format on enter, <cr> could be remapped by other vim plugin
inoremap <silent><expr> <cr> pumvisible() ? coc#_select_confirm()
                              \: "\<C-g>u\<CR>\<c-r>=coc#on_enter()\<CR>"

" Use `[g` and `]g` to navigate diagnostics
" Use `:CocDiagnostics` to get all diagnostics of current buffer in location list.
nmap <silent> [g <Plug>(coc-diagnostic-prev)
nmap <silent> ]g <Plug>(coc-diagnostic-next)

" GoTo code navigation.
nmap <silent> gd <Plug>(coc-definition)
nmap <silent> gy <Plug>(coc-type-definition)
nmap <silent> gi <Plug>(coc-implementation)
nmap <silent> gr <Plug>(coc-references)

" Use K to show documentation in preview window.
nnoremap <silent> K :call <SID>show_documentation()<CR>

function! s:show_documentation()
  if (index(['vim','help'], &filetype) >= 0)
    execute 'h '.expand('<cword>')
  elseif (coc#rpc#ready())
    call CocActionAsync('doHover')
  else
    execute '!' . &keywordprg . " " . expand('<cword>')
  endif
endfunction

" Highlight the symbol and its references when holding the cursor.
autocmd CursorHold * silent call CocActionAsync('highlight')

" Symbol renaming.
nmap <leader>rn <Plug>(coc-rename)

" Formatting selected code.
xmap <leader>f  <Plug>(coc-format-selected)
nmap <leader>f  <Plug>(coc-format-selected)

augroup mygroup
  autocmd!
  " Setup formatexpr specified filetype(s).
  autocmd FileType typescript,json setl formatexpr=CocAction('formatSelected')
  " Update signature help on jump placeholder.
  autocmd User CocJumpPlaceholder call CocActionAsync('showSignatureHelp')
augroup end

" Applying codeAction to the selected region.
" Example: `<leader>aap` for current paragraph
xmap <leader>a  <Plug>(coc-codeaction-selected)
nmap <leader>a  <Plug>(coc-codeaction-selected)

" Remap keys for applying codeAction to the current buffer.
nmap <leader>ac  <Plug>(coc-codeaction)
" Apply AutoFix to problem on the current line.
nmap <leader>qf  <Plug>(coc-fix-current)

" Map function and class text objects
" NOTE: Requires 'textDocument.documentSymbol' support from the language server.
xmap if <Plug>(coc-funcobj-i)
omap if <Plug>(coc-funcobj-i)
xmap af <Plug>(coc-funcobj-a)
omap af <Plug>(coc-funcobj-a)
xmap ic <Plug>(coc-classobj-i)
omap ic <Plug>(coc-classobj-i)
xmap ac <Plug>(coc-classobj-a)
omap ac <Plug>(coc-classobj-a)

" Remap <C-f> and <C-b> for scroll float windows/popups.
if has('nvim-0.4.0') || has('patch-8.2.0750')
  nnoremap <silent><nowait><expr> <C-f> coc#float#has_scroll() ? coc#float#scroll(1) : "\<C-f>"
  nnoremap <silent><nowait><expr> <C-b> coc#float#has_scroll() ? coc#float#scroll(0) : "\<C-b>"
  inoremap <silent><nowait><expr> <C-f> coc#float#has_scroll() ? "\<c-r>=coc#float#scroll(1)\<cr>" : "\<Right>"
  inoremap <silent><nowait><expr> <C-b> coc#float#has_scroll() ? "\<c-r>=coc#float#scroll(0)\<cr>" : "\<Left>"
  vnoremap <silent><nowait><expr> <C-f> coc#float#has_scroll() ? coc#float#scroll(1) : "\<C-f>"
  vnoremap <silent><nowait><expr> <C-b> coc#float#has_scroll() ? coc#float#scroll(0) : "\<C-b>"
endif

" Use CTRL-S for selections ranges.
" Requires 'textDocument/selectionRange' support of language server.
nmap <silent> <C-s> <Plug>(coc-range-select)
xmap <silent> <C-s> <Plug>(coc-range-select)

" Add `:Format` command to format current buffer.
command! -nargs=0 Format :call CocAction('format')

" Add `:Fold` command to fold current buffer.
command! -nargs=? Fold :call     CocAction('fold', <f-args>)

" Add `:OR` command for organize imports of the current buffer.
command! -nargs=0 OR   :call     CocAction('runCommand', 'editor.action.organizeImport')

" Add (Neo)Vim's native statusline support.
" NOTE: Please see `:h coc-status` for integrations with external plugins that
" provide custom statusline: lightline.vim, vim-airline.
set statusline^=%{coc#status()}%{get(b:,'coc_current_function','')}

" Mappings for CoCList
" Show all diagnostics.
nnoremap <silent><nowait> <space>a  :<C-u>CocList diagnostics<cr>
" Manage extensions.
nnoremap <silent><nowait> <space>e  :<C-u>CocList extensions<cr>
" Show commands.
nnoremap <silent><nowait> <space>c  :<C-u>CocList commands<cr>
" Find symbol of current document.
nnoremap <silent><nowait> <space>o  :<C-u>CocList outline<cr>
" Search workspace symbols.
nnoremap <silent><nowait> <space>s  :<C-u>CocList -I symbols<cr>
" Do default action for next item.
nnoremap <silent><nowait> <space>j  :<C-u>CocNext<CR>
" Do default action for previous item.
nnoremap <silent><nowait> <space>k  :<C-u>CocPrev<CR>
" Resume latest coc list.
nnoremap <silent><nowait> <space>p  :<C-u>CocListResume<CR>
```

## Articles

- [coc.nvim 插件体系介绍](https://zhuanlan.zhihu.com/p/65524706)
- [CocList 入坑指南](https://zhuanlan.zhihu.com/p/71846145)
- [Create coc.nvim extension to improve Vim experience](https://medium.com/@chemzqm/create-coc-nvim-extension-to-improve-vim-experience-4461df269173)
- [How to write a coc.nvim extension (and why)](https://samroeca.com/coc-plugin.html)

## Trouble shooting

Try these steps when you have problem with coc.nvim.

- Make sure your Vim version >= 8.0 by command `:version`.
- If service failed to start, use command `:CocInfo` or `:checkhealth` on Neovim.
- Checkout the log of coc.nvim by command `:CocOpenLog`.
- When you have issues with the language server, it's recommended to [checkout
  the output](https://github.com/neoclide/coc.nvim/wiki/Debug-language-server#using-output-channel).

## Feedback

- If you think Coc is useful, consider giving it a star.
- If you have a question, [ask on gitter](https://gitter.im/neoclide/coc.nvim)
- 中文用户请到 [中文 gitter](https://gitter.im/neoclide/coc-cn) 讨论
- If something is not working, [create an
  issue](https://github.com/neoclide/coc.nvim/issues/new).

## Backers

[Become a backer](https://opencollective.com/cocnvim#backer) and get your image on our README on Github with a link to your site.

<a href="https://opencollective.com/cocnvim/backer/0/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/0/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/1/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/1/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/2/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/2/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/3/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/3/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/4/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/4/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/5/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/5/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/6/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/6/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/7/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/7/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/8/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/8/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/9/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/9/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/10/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/10/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/11/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/11/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/12/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/12/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/13/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/13/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/14/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/14/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/15/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/15/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/16/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/16/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/cocnvim/backer/17/website?requireActive=false" target="_blank"><img src="https://opencollective.com/cocnvim/backer/17/avatar.svg?requireActive=false"></a>

<a href="https://opencollective.com/cocnvim#backer" target="_blank"><img src="https://images.opencollective.com/static/images/become_backer.svg"></a>

## License

MIT

# Dracula for [Vim](http://www.vim.org/)

> A dark theme for [Vim](http://www.vim.org/).

![Screenshot](./screenshot.png)

Screenshot taken with the [pangloss/vim-javascript](https://github.com/pangloss/vim-javascript)
syntax plugin for javascript.

## Install

All instructions can be found at [draculatheme.com/vim](https://draculatheme.com/vim).

## Team

This theme is maintained by the following person(s) and a bunch of
[awesome contributors](https://github.com/dracula/vim/graphs/contributors).

| [![Derek S.](https://avatars3.githubusercontent.com/u/5240018?v=3&s=70)](https://github.com/dsifford) | [![David Knoble](https://avatars0.githubusercontent.com/u/22802209?v=4&s=70)](https://github.com/benknoble) |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| [Derek S.](https://github.com/dsifford)                                                               | [David Knoble](https://github.com/benknoble)                                                                |

## License

[MIT License](./LICENSE)

Fantasque Sans Mono
===================

A programming font, designed with functionality in mind, and with some
wibbly-wobbly handwriting-like fuzziness that makes it unassumingly cool.
[Download](https://github.com/belluzj/fantasque-sans/releases/latest) or 
see [installation instructions](#installation).


![](Specimen/urxvt13.png)

Previously known as *Cosmic Sans Neue Mono*. It
appeared that [similar names were already in use for other
fonts](https://github.com/belluzj/cosmic-sans-neue/issues/16), and that
people tended to extend their instinctive hatred of Comic Sans to this very
font of mine (which of course can only be *loved*). Why the previous name?
Here is my original explanation:

> The name comes from my realization that at some point it looked like the
> mutant child of Comic Sans and Helvetica Neue. Hopefully it is not the
> case any more.

Inspirational sources include Inconsolata and Monaco. I have also been using
Consolas a lot in my programming life, so it may have some points in common.

![](Specimen/kdevelop11.png)
![](Specimen/sublime11.png)

Weights, variants and glyph coverage
------------------------------------

The font includes a bold version, with the same metrics as the regular one.
Both versions include the same ranges of characters : latin letters, some
accented glyphs (quite a lot), some greek letters, some arrows.

Please note that I have not tested all of the glyphs I have drawn (some letters
have those two layers of crazy accents that I have never witnessed before), so
it might look bad in some cases. Please report these problems: see next section.

It also features a good italic version, which I designed in a fashion similar
to Consolas' italic version, with new glyph designs, not just an added slant.

![](Specimen/vim21.png)

Stylistic set(s)
----------------

### `ss01`: nondescript `k`

No ~~distractive~~ lovely loop.
[Get the pre-activated version here](https://github.com/belluzj/fantasque-sans/releases/download/1.8.0/FantasqueSansMono-NoLoopK.zip)
or see the [issue #67](https://github.com/belluzj/fantasque-sans/issues/67)
for techniques to activate the stylistic set.

![](Specimen/noloopk.png)

Author and license
------------------

Created by Jany Belluz \<jany.belluz AT hotmail.fr\>

Licensed under the SIL Open Font License (see [LICENSE.txt](LICENSE.txt)).

Please send me an e-mail or [report an issue on
Github](http://github.com/belluzj/cosmic-sans-neue/issues) if you stumble upon
bad design or rendering problems (with screen shot if possible), or if you need
more characters, or if you want to compliment me (I love compliments).

Installation
------------

You can [download the latest version](https://github.com/belluzj/fantasque-sans/releases/latest)
and install it by hand. In the `NoLoopK` variant, the looped lowercase `k` is 
replaced with a straight version. The `LargeLineHeight` variant is especially 
useful for users of accented capitals. For more info, see the [CHANGELOG](CHANGELOG.md).

Automatic installation on macOS with [homebrew](https://brew.sh):

    brew tap homebrew/cask-fonts #You only need to do this once for cask-fonts
    brew install --cask font-fantasque-sans-mono

Instructions for other platforms might follow.

Building installable font files
-------------------------------

The build process requires:
* FontForge with python scripting support,
* `ttfautohint`
* `sfnt2woff` (from the `woff-tools` package on Ubuntu)
* `woff2_compress` from [the Google WOFF2
  tools](https://github.com/google/woff2) or `woff2` package on Ubuntu

Run `make`. You should see green stuff and some "OK" messages.

If you are using Ubuntu, please note that the FontForge version
in the default Ubuntu repositories is much outdated at the time of this writing,
and that [is known to have caused subtle problems](https://github.com/belluzj/fantasque-sans/issues/59).
You are advised to install FontForge from
[this PPA](https://launchpad.net/~fontforge/+archive/ubuntu/fontforge)
(using `sudo add-apt-repository ppa:fontforge/fontforge` prior to the installation).
Alternatively, you can always [download](https://github.com/belluzj/fantasque-sans/releases/latest)
the latest prebuilt release of these fonts.

`make install` will install the TTF fonts into your local `.fonts/` directory
and update the font cache. It comes in handy while modifying the font.

Alternatively, if you'd like to build Fantasque without installing required
dependencies, a Dockerfile is provided. Run the following command, and the
fonts will be built to the `./Variants` directory.

```sh
docker build -t fantasque .
docker run -v "$(pwd)/Variants:/fantasque/Variants" fantasque
```

[![](Specimen/Specimen.png)](Specimen/Specimen.pdf)

Webfonts
--------

Each variant has a `Webfonts/` folder which contains various font formats for
use on the web, along with the matching CSS font declarations. To use them,
you must combine in the same folder:
* a custom `.css` file that you can assemble from the `*-decl.css` fragments
  (you can only pick the styles that you need, e.g. normal and bold)
* the matching `.svg`, `.woff`, `.woff2` files from `Webfonts/`
* the matching `.ttf` files from the `TTF/` folder
* the matching `.otf` files from the `OTF/` folder.

Versions
--------

[Check out the changelog](CHANGELOG.md).

# The NERDTree [![Vint](https://github.com/preservim/nerdtree/workflows/Vint/badge.svg)](https://github.com/preservim/nerdtree/actions?workflow=Vint)

## Introduction

The NERDTree is a file system explorer for the Vim editor. Using this plugin, users can visually browse complex directory hierarchies, quickly open files for reading or editing, and perform basic file system operations.

![NERDTree Screenshot](https://github.com/preservim/nerdtree/raw/master/screenshot.png)

## Installation

Use your favorite plugin manager to install this plugin. [tpope/vim-pathogen](https://github.com/tpope/vim-pathogen), [VundleVim/Vundle.vim](https://github.com/VundleVim/Vundle.vim), [junegunn/vim-plug](https://github.com/junegunn/vim-plug), and [Shougo/dein.vim](https://github.com/Shougo/dein.vim) are some of the more popular ones. A lengthy discussion of these and other managers can be found on [vi.stackexchange.com](https://vi.stackexchange.com/questions/388/what-is-the-difference-between-the-vim-plugin-managers). Basic instructions are provided below, but please **be sure to read, understand, and follow all the safety rules that come with your ~~power tools~~ plugin manager.**

If you have no favorite, or want to manage your plugins without 3rd-party dependencies, consider using Vim 8+ packages, as described in Greg Hurrell's excellent Youtube video: [Vim screencast #75: Plugin managers](https://www.youtube.com/watch?v=X2_R3uxDN6g).

<details>
<summary>Pathogen</summary>
Pathogen is more of a runtime path manager than a plugin manager. You must clone the plugins' repositories yourself to a specific location, and Pathogen makes sure they are available in Vim.


1. In the terminal,
    ```bash
    git clone https://github.com/preservim/nerdtree.git ~/.vim/bundle/nerdtree
    ```
1. In your `vimrc`,
    ```vim
    call pathogen#infect()
    syntax on
    filetype plugin indent on
    ```
1. Restart Vim, and run `:helptags ~/.vim/bundle/nerdtree/doc/` or `:Helptags`.
</details>

<details>
  <summary>Vundle</summary>

1. Install Vundle, according to its instructions.
1. Add the following text to your `vimrc`.
    ```vim
    call vundle#begin()
      Plugin 'preservim/nerdtree'
    call vundle#end()
    ```
1. Restart Vim, and run the `:PluginInstall` statement to install your plugins.
</details>

<details>
  <summary>Vim-Plug</summary>

1. Install Vim-Plug, according to its instructions.
1. Add the following text to your `vimrc`.
```vim
call plug#begin()
  Plug 'preservim/nerdtree'
call plug#end()
```
1. Restart Vim, and run the `:PlugInstall` statement to install your plugins.
</details>

<details>
  <summary>Dein</summary>

1. Install Dein, according to its instructions.
1. Add the following text to your `vimrc`.
    ```vim
    call dein#begin()
      call dein#add('preservim/nerdtree')
    call dein#end()
    ```
1. Restart Vim, and run the `:call dein#install()` statement to install your plugins.
</details>

<details>
<summary>Vim 8+ packages</summary>

If you are using Vim version 8 or higher you can use its built-in package management; see `:help packages` for more information. Just run these commands in your terminal:

```bash
git clone https://github.com/preservim/nerdtree.git ~/.vim/pack/vendor/start/nerdtree
vim -u NONE -c "helptags ~/.vim/pack/vendor/start/nerdtree/doc" -c q
```
</details>

## Getting Started
After installing NERDTree, the best way to learn it is to turn on the Quick Help. Open NERDTree with the `:NERDTree` command, and press `?` to turn on the Quick Help, which will show you all the mappings and commands available in the NERDTree. Of course, your most complete source of information is the documentation: `:help NERDTree`.

## NERDTree Plugins
NERDTree can be extended with custom mappings and functions using its built-in API. The details of this API and are described in the included documentation. Several plugins have been written, and are available on Github for installation like any other plugin. The plugins in this list are maintained (or not) by their respective owners, and certain combinations may be incompatible.

* [Xuyuanp/nerdtree-git-plugin](https://github.com/Xuyuanp/nerdtree-git-plugin): Shows Git status flags for files and folders in NERDTree.
* [ryanoasis/vim-devicons](https://github.com/ryanoasis/vim-devicons): Adds filetype-specific icons to NERDTree files and folders,
* [tiagofumo/vim-nerdtree-syntax-highlight](https://github.com/tiagofumo/vim-nerdtree-syntax-highlight): Adds syntax highlighting to NERDTree based on filetype.
* [scrooloose/nerdtree-project-plugin](https://github.com/scrooloose/nerdtree-project-plugin): Saves and restores the state of the NERDTree between sessions.
* [PhilRunninger/nerdtree-buffer-ops](https://github.com/PhilRunninger/nerdtree-buffer-ops): 1) Highlights open files in a different color. 2) Closes a buffer directly from NERDTree.
* [PhilRunninger/nerdtree-visual-selection](https://github.com/PhilRunninger/nerdtree-visual-selection): Enables NERDTree to open, delete, move, or copy multiple Visually-selected files at once.

If any others should be listed, mention them in an issue or pull request.


## Frequently Asked Questions

In the answers to these questions, you will see code blocks that you can put in your `vimrc` file.

### How can I map a specific key or shortcut to open NERDTree?

NERDTree doesn't create any shortcuts outside of the NERDTree window, so as not to overwrite any of your other shortcuts. Use the `nnoremap` command in your `vimrc`. You, of course, have many keys and NERDTree commands to choose from. Here are but a few examples.
```vim
nnoremap <leader>n :NERDTreeFocus<CR>
nnoremap <C-n> :NERDTree<CR>
nnoremap <C-t> :NERDTreeToggle<CR>
nnoremap <C-f> :NERDTreeFind<CR>
```

### How do I open NERDTree automatically when Vim starts?
Each code block below is slightly different, as described in the `" Comment lines`.

```vim
" Start NERDTree and leave the cursor in it.
autocmd VimEnter * NERDTree
```
---
```vim
" Start NERDTree and put the cursor back in the other window.
autocmd VimEnter * NERDTree | wincmd p
```
---
```vim
" Start NERDTree when Vim is started without file arguments.
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 0 && !exists('s:std_in') | NERDTree | endif
```
---
```vim
" Start NERDTree. If a file is specified, move the cursor to its window.
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * NERDTree | if argc() > 0 || exists("s:std_in") | wincmd p | endif
```
---
```vim
" Start NERDTree, unless a file or session is specified, eg. vim -S session_file.vim.
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 0 && !exists('s:std_in') && v:this_session == '' | NERDTree | endif
```
---
```vim
" Start NERDTree when Vim starts with a directory argument.
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 1 && isdirectory(argv()[0]) && !exists('s:std_in') |
    \ execute 'NERDTree' argv()[0] | wincmd p | enew | execute 'cd '.argv()[0] | endif
```

### How can I close Vim automatically when NERDTree is the last window?

```vim
" Exit Vim if NERDTree is the only window left.
autocmd BufEnter * if tabpagenr('$') == 1 && winnr('$') == 1 && exists('b:NERDTree') && b:NERDTree.isTabTree() |
    \ quit | endif
```

### How can I prevent other buffers replacing NERDTree in its window?

```vim
" If another buffer tries to replace NERDTree, put it in the other window, and bring back NERDTree.
autocmd BufEnter * if bufname('#') =~ 'NERD_tree_\d\+' && bufname('%') !~ 'NERD_tree_\d\+' && winnr('$') > 1 |
    \ let buf=bufnr() | buffer# | execute "normal! \<C-W>w" | execute 'buffer'.buf | endif
```

### Can I have the same NERDTree on every tab automatically?

```vim
" Open the existing NERDTree on each new tab.
autocmd BufWinEnter * silent NERDTreeMirror
```
or change your NERDTree-launching shortcut key like so:
```vim
" Mirror the NERDTree before showing it. This makes it the same on all tabs.
nnoremap <C-n> :NERDTreeMirror<CR>:NERDTreeFocus<CR>
```

### How can I change the default arrows?

```vim
let g:NERDTreeDirArrowExpandable = '▸'
let g:NERDTreeDirArrowCollapsible = '▾'
```
The preceding values are the non-Windows default arrow symbols. Setting these variables to empty strings will remove the arrows completely and shift the entire tree two character positions to the left. See `:h NERDTreeDirArrowExpandable` for more details.

# vim-airline 

[![Say Thanks!](https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg)](https://saythanks.io/to/cb%40256bit.org)
[![reviewdog](https://github.com/vim-airline/vim-airline/workflows/reviewdog/badge.svg?branch=master&event=push)](https://github.com/vim-airline/vim-airline/actions?query=workflow%3Areviewdog+event%3Apush+branch%3Amaster)
[![CI](https://github.com/vim-airline/vim-airline/workflows/CI/badge.svg)](https://github.com/vim-airline/vim-airline/actions?query=workflow%3ACI)

Lean & mean status/tabline for vim that's light as air.

![img](https://github.com/vim-airline/vim-airline/wiki/screenshots/demo.gif)

When the plugin is correctly loaded, there will be a nice statusline at the
bottom of each vim window.

That line consists of several sections, each one displaying some piece of
information. By default (without configuration) this line will look like this:

```
+-----------------------------------------------------------------------------+
|~                                                                            |
|~                                                                            |
|~                     VIM - Vi IMproved                                      |
|~                                                                            |
|~                       version 8.2                                          |
|~                    by Bram Moolenaar et al.                                |
|~           Vim is open source and freely distributable                      |
|~                                                                            |
|~           type :h :q<Enter>          to exit                               |
|~           type :help<Enter> or <F1>  for on-line help                      |
|~           type :help version8<Enter> for version info                      |
|~                                                                            |
|~                                                                            |
+-----------------------------------------------------------------------------+
| A | B |                     C                            X | Y | Z |  [...] |
+-----------------------------------------------------------------------------+
```

The statusline is the colored line at the bottom, which contains the sections
(possibly in different colors):

section|meaning (example)
-------|------------------
  A    | displays the mode + additional flags like crypt/spell/paste (INSERT)
  B    | Environment status (VCS information - branch, hunk summary (master), [battery][61] level)
  C    | filename + read-only flag (~/.vim/vimrc RO)
  X    | filetype  (vim)
  Y    | file encoding[fileformat] (utf-8[unix])
  Z    | current position in the file
 [...] | additional sections (warning/errors/statistics) from external plugins (e.g. YCM, syntastic, ...)

The information in Section Z looks like this:

`10% ☰ 10/100 ln : 20`

This means:
```
10%     - 10 percent down the top of the file
☰ 10    - current line 10
/100 ln - of 100 lines
: 20    - current column 20
```

For a better look, those sections can be colored differently, depending on various conditions
(e.g. the mode or whether the current file is 'modified')

# Features

*  Tiny core written with extensibility in mind ([open/closed principle][8]).
*  Integrates with a variety of plugins, including: [vim-bufferline][6],
   [fugitive][4], [unite][9], [ctrlp][10], [minibufexpl][15], [gundo][16],
   [undotree][17], [nerdtree][18], [tagbar][19], [vim-gitgutter][29],
   [vim-signify][30], [quickfixsigns][39], [syntastic][5], [eclim][34],
   [lawrencium][21], [virtualenv][31], [tmuxline][35], [taboo.vim][37],
   [ctrlspace][38], [vim-bufmru][47], [vimagit][50], [denite][51],
   [vim.battery][61] and more.
*  Looks good with regular fonts and provides configuration points so you can use unicode or powerline symbols.
*  Optimized for speed - loads in under a millisecond.
*  Extensive suite of themes for popular color schemes including [solarized][23] (dark and light), [tomorrow][24] (all variants), [base16][32] (all variants), [molokai][25], [jellybeans][26] and others.
 Note these are now external to this plugin. More details can be found in the [themes repository][46].
*  Supports 7.2 as the minimum Vim version.
*  The master branch tries to be as stable as possible, and new features are merged in only after they have gone through a [full regression test][33].
*  Unit testing suite.

## Straightforward customization

If you don't like the defaults, you can replace all sections with standard `statusline` syntax.  Give your statusline that you've built over the years a face lift.

![image](https://f.cloud.github.com/assets/306502/1009429/d69306da-0b38-11e3-94bf-7c6e3eef41e9.png)

## Themes

Themes have moved to
another repository as of [this commit][45].

Install the themes as you would this plugin (Vundle example):

```vim
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'
```

See [vim-airline-themes][46] for more.

## Automatic truncation

Sections and parts within sections can be configured to automatically hide when the window size shrinks.

![image](https://f.cloud.github.com/assets/306502/1060831/05c08aac-11bc-11e3-8470-a506a3037f45.png)

## Smarter tab line

Automatically displays all buffers when there's only one tab open.

![tabline](https://f.cloud.github.com/assets/306502/1072623/44c292a0-1495-11e3-9ce6-dcada3f1c536.gif)

This is disabled by default; add the following to your vimrc to enable the extension:

    let g:airline#extensions#tabline#enabled = 1

Separators can be configured independently for the tabline, so here is how you can define "straight" tabs:

    let g:airline#extensions#tabline#left_sep = ' '
    let g:airline#extensions#tabline#left_alt_sep = '|'

In addition, you can also choose which path formatter airline uses. This affects how file paths are
displayed in each individual tab as well as the current buffer indicator in the upper right.
To do so, set the `formatter` field with:

    let g:airline#extensions#tabline#formatter = 'default'

Here is a complete list of formatters with screenshots:

#### `default`
![image](https://user-images.githubusercontent.com/2652762/34422844-1d005efa-ebe6-11e7-8053-c784c0da7ba7.png)

#### `jsformatter`
![image](https://user-images.githubusercontent.com/2652762/34422843-1cf6a4d2-ebe6-11e7-810a-07e6eb08de24.png)

#### `unique_tail`
![image](https://user-images.githubusercontent.com/2652762/34422841-1ce5b4ec-ebe6-11e7-86e9-3d45c876068b.png)

#### `unique_tail_improved`
![image](https://user-images.githubusercontent.com/2652762/34422842-1cee23f2-ebe6-11e7-962d-97e068873077.png)

## Seamless integration

vim-airline integrates with a variety of plugins out of the box.  These extensions will be lazily loaded if and only if you have the other plugins installed (and of course you can turn them off).

#### [ctrlp.vim][10]
![image](https://f.cloud.github.com/assets/306502/962258/7345a224-04ec-11e3-8b5a-f11724a47437.png)

#### [unite.vim][9]
![image](https://f.cloud.github.com/assets/306502/962319/4d7d3a7e-04ed-11e3-9d59-ab29cb310ff8.png)

#### [denite.nvim][51]
![image](https://cloud.githubusercontent.com/assets/246230/23939717/f65bce6e-099c-11e7-85c3-918dbc839392.png)

#### [tagbar][19]
![image](https://f.cloud.github.com/assets/306502/962150/7e7bfae6-04ea-11e3-9e28-32af206aed80.png)

#### [csv.vim][28]
![image](https://f.cloud.github.com/assets/306502/962204/cfc1210a-04eb-11e3-8a93-42e6bcd21efa.png)

#### [syntastic][5]
![image](https://f.cloud.github.com/assets/306502/962864/9824c484-04f7-11e3-9928-da94f8c7da5a.png)

#### hunks ([vim-gitgutter][29] & [vim-signify][30] & [coc-git][59])
![image](https://f.cloud.github.com/assets/306502/995185/73fc7054-09b9-11e3-9d45-618406c6ed98.png)

#### [vimagit][50]
![vim-airline-vimagit-demo](https://cloud.githubusercontent.com/assets/533068/22107273/2ea85ba0-de4d-11e6-9fa8-331103b88df4.gif)

#### [virtualenv][31]
![image](https://f.cloud.github.com/assets/390964/1022566/cf81f830-0d98-11e3-904f-cf4fe3ce201e.png)

#### [tmuxline][35]
![image](https://f.cloud.github.com/assets/1532071/1559276/4c28fbac-4fc7-11e3-90ef-7e833d980f98.gif)

#### [promptline][36]
![airline-promptline-sc](https://f.cloud.github.com/assets/1532071/1871900/7d4b28a0-789d-11e3-90e4-16f37269981b.gif)

#### [ctrlspace][38]
![papercolor_with_ctrlspace](https://cloud.githubusercontent.com/assets/493242/12912041/7fc3c6ec-cf16-11e5-8775-8492b9c64ebf.png)

#### [xkb-switch][48]/[xkb-layout][49]
![image](https://cloud.githubusercontent.com/assets/5715281/22061422/347e7842-ddb8-11e6-8bdb-7abbd418653c.gif)

#### [vimtex][53]
![image](https://cloud.githubusercontent.com/assets/1798172/25799740/e77d5c2e-33ee-11e7-8660-d34ce4c5f13f.png)

#### [localsearch][54]
![image](https://raw.githubusercontent.com/mox-mox/vim-localsearch/master/vim-airline-localsearch-indicator.png)

#### [LanguageClient][57]
![image](https://user-images.githubusercontent.com/9622/45275524-52f45c00-b48b-11e8-8b83-a66240b10747.gif)

#### [Vim-CMake][60]
![image](https://user-images.githubusercontent.com/24732205/87788512-c876a380-c83d-11ea-9ee3-5f639f986a8f.png)

#### [vim.battery][61]
![image](https://user-images.githubusercontent.com/1969470/94561399-368b0e00-0264-11eb-94a0-f6b67c73d422.png)

## Extras

vim-airline also supplies some supplementary stand-alone extensions.  In addition to the tabline extension mentioned earlier, there is also:

#### whitespace
![image](https://f.cloud.github.com/assets/306502/962401/2a75385e-04ef-11e3-935c-e3b9f0e954cc.png)

### statusline on top
The statusline can alternatively be drawn on top, making room for other plugins to use the statusline:
The example shows a custom statusline setting, that imitates Vims default statusline, while allowing
to call custom functions.  Use `:let g:airline_statusline_ontop=1` to enable it.

![image](https://i.imgur.com/tW1lMRU.png)

## Configurable and extensible

#### Fine-tuned configuration

Every section is composed of parts, and you can reorder and reconfigure them at will.

![image](https://f.cloud.github.com/assets/306502/1073278/f291dd4c-14a3-11e3-8a83-268e2753f97d.png)

Sections can contain accents, which allows for very granular control of visuals (see configuration [here](https://github.com/vim-airline/vim-airline/issues/299#issuecomment-25772886)).

![image](https://f.cloud.github.com/assets/306502/1195815/4bfa38d0-249d-11e3-823e-773cfc2ca894.png)

#### Extensible pipeline

Completely transform the statusline to your liking.  Build out the statusline as you see fit by extracting colors from the current colorscheme's highlight groups.

![allyourbase](https://f.cloud.github.com/assets/306502/1022714/e150034a-0da7-11e3-94a5-ca9d58a297e8.png)

# Rationale

There's already [powerline][2], why yet another statusline?

*  100% vimscript; no python needed.

What about [vim-powerline][1]?

*  vim-powerline has been deprecated in favor of the newer, unifying powerline, which is under active development; the new version is written in python at the core and exposes various bindings such that it can style statuslines not only in vim, but also tmux, bash, zsh, and others.

# Where did the name come from?

I wrote the initial version on an airplane, and since it's light as air it turned out to be a good name.  Thanks for flying vim!

# Installation

This plugin follows the standard runtime path structure, and as such it can be installed with a variety of plugin managers:

| Plugin Manager | Install with... |
| ------------- | ------------- |
| [Pathogen][11] | `git clone https://github.com/vim-airline/vim-airline ~/.vim/bundle/vim-airline`<br/>Remember to run `:Helptags` to generate help tags |
| [NeoBundle][12] | `NeoBundle 'vim-airline/vim-airline'` |
| [Vundle][13] | `Plugin 'vim-airline/vim-airline'` |
| [Plug][40] | `Plug 'vim-airline/vim-airline'` |
| [VAM][22] | `call vam#ActivateAddons([ 'vim-airline' ])` |
| [Dein][52] | `call dein#add('vim-airline/vim-airline')` |
| [minpac][55] | `call minpac#add('vim-airline/vim-airline')` |
| pack feature (native Vim 8 package feature)| `git clone https://github.com/vim-airline/vim-airline ~/.vim/pack/dist/start/vim-airline`<br/>Remember to run `:helptags ~/.vim/pack/dist/start/vim-airline/doc` to generate help tags |
| manual | copy all of the files into your `~/.vim` directory |

# Documentation

`:help airline`

# Integrating with powerline fonts

For the nice looking powerline symbols to appear, you will need to install a patched font.  Instructions can be found in the official powerline [documentation][20].  Prepatched fonts can be found in the [powerline-fonts][3] repository.

Finally, you can add the convenience variable `let g:airline_powerline_fonts = 1` to your vimrc which will automatically populate the `g:airline_symbols` dictionary with the powerline symbols.

# FAQ

Solutions to common problems can be found in the [Wiki][27].

# Performance

Whoa! Everything got slow all of a sudden...

vim-airline strives to make it easy to use out of the box, which means that by default it will look for all compatible plugins that you have installed and enable the relevant extension.

Many optimizations have been made such that the majority of users will not see any performance degradation, but it can still happen.  For example, users who routinely open very large files may want to disable the `tagbar` extension, as it can be very expensive to scan for the name of the current function.

The [minivimrc][7] project has some helper mappings to troubleshoot performance related issues.

If you don't want all the bells and whistles enabled by default, you can define a value for `g:airline_extensions`.  When this variable is defined, only the extensions listed will be loaded; an empty array would effectively disable all extensions (e.g. `:let g:airline_extensions = []`).

Also, you can enable caching of the various syntax highlighting groups. This will try to prevent some of the more expensive `:hi` calls in Vim, which seem to be expensive in the Vim core at the expense of possibly not being one hundred percent correct all the time (especially if you often change highlighting groups yourself using `:hi` commands). To set this up do `:let g:airline_highlighting_cache = 1`. A `:AirlineRefresh` will however clear the cache.

In addition you might want to check out the [dark_minimal theme][56], which does not change highlighting groups once they are defined. Also please check the [FAQ][27] for more information on how to diagnose and fix the problem.

# Screenshots

A full list of screenshots for various themes can be found in the [Wiki][14].

# Maintainers

The project is currently being maintained by [Christian Brabandt][42] and [Bailey Ling][41].

If you are interested in becoming a maintainer (we always welcome more maintainers), please [go here][43].

# License

[MIT License][58]. Copyright (c) 2013-2021 Bailey Ling & Contributors.

[1]: https://github.com/Lokaltog/vim-powerline
[2]: https://github.com/Lokaltog/powerline
[3]: https://github.com/Lokaltog/powerline-fonts
[4]: https://github.com/tpope/vim-fugitive
[5]: https://github.com/scrooloose/syntastic
[6]: https://github.com/bling/vim-bufferline
[7]: https://github.com/bling/minivimrc
[8]: http://en.wikipedia.org/wiki/Open/closed_principle
[9]: https://github.com/Shougo/unite.vim
[10]: https://github.com/ctrlpvim/ctrlp.vim
[11]: https://github.com/tpope/vim-pathogen
[12]: https://github.com/Shougo/neobundle.vim
[13]: https://github.com/VundleVim/Vundle.vim
[14]: https://github.com/vim-airline/vim-airline/wiki/Screenshots
[15]: https://github.com/techlivezheng/vim-plugin-minibufexpl
[16]: https://github.com/sjl/gundo.vim
[17]: https://github.com/mbbill/undotree
[18]: https://github.com/preservim/nerdtree
[19]: https://github.com/majutsushi/tagbar
[20]: https://powerline.readthedocs.org/en/master/installation.html#patched-fonts
[21]: https://github.com/ludovicchabant/vim-lawrencium
[22]: https://github.com/MarcWeber/vim-addon-manager
[23]: https://github.com/altercation/solarized
[24]: https://github.com/chriskempson/tomorrow-theme
[25]: https://github.com/tomasr/molokai
[26]: https://github.com/nanotech/jellybeans.vim
[27]: https://github.com/vim-airline/vim-airline/wiki/FAQ
[28]: https://github.com/chrisbra/csv.vim
[29]: https://github.com/airblade/vim-gitgutter
[30]: https://github.com/mhinz/vim-signify
[31]: https://github.com/jmcantrell/vim-virtualenv
[32]: https://github.com/chriskempson/base16-vim
[33]: https://github.com/vim-airline/vim-airline/wiki/Test-Plan
[34]: http://eclim.org
[35]: https://github.com/edkolev/tmuxline.vim
[36]: https://github.com/edkolev/promptline.vim
[37]: https://github.com/gcmt/taboo.vim
[38]: https://github.com/vim-ctrlspace/vim-ctrlspace
[39]: https://github.com/tomtom/quickfixsigns_vim
[40]: https://github.com/junegunn/vim-plug
[41]: https://github.com/bling
[42]: https://github.com/chrisbra
[43]: https://github.com/vim-airline/vim-airline/wiki/Becoming-a-Maintainer
[45]: https://github.com/vim-airline/vim-airline/commit/d7fd8ca649e441b3865551a325b10504cdf0711b
[46]: https://github.com/vim-airline/vim-airline-themes#vim-airline-themes--
[47]: https://github.com/mildred/vim-bufmru
[48]: https://github.com/ierton/xkb-switch
[49]: https://github.com/vovkasm/input-source-switcher
[50]: https://github.com/jreybert/vimagit
[51]: https://github.com/Shougo/denite.nvim
[52]: https://github.com/Shougo/dein.vim
[53]: https://github.com/lervag/vimtex
[54]: https://github.com/mox-mox/vim-localsearch
[55]: https://github.com/k-takata/minpac/
[56]: https://github.com/vim-airline/vim-airline-themes/blob/master/autoload/airline/themes/dark_minimal.vim
[57]: https://github.com/autozimu/LanguageClient-neovim
[58]: https://github.com/vim-airline/vim-airline/blob/master/LICENSE
[59]: https://github.com/neoclide/coc-git
[60]: https://github.com/cdelledonne/vim-cmake
[61]: http://github.com/lambdalisue/battery.vim/

vim.cpp - additional vim c++ syntax highlighting
------------------------------------------------

This file contains additional syntax highlighting that I use for C++11/14/17
development in Vim. Compared to the standard syntax highlighting for C++ it
adds highlighting of (user defined) functions and the containers and types in
the standard library / boost.

Development is done at: http://github.com/octol/vim-cpp-enhanced-highlight

![Screenshot](http://www.haeggblad.com/vim/screenshot.png)

Optional features
-----------------

Highlighting of class scope is disabled by default. To enable set
```vim
let g:cpp_class_scope_highlight = 1
```

Highlighting of member variables is disabled by default. To enable set
```vim
let g:cpp_member_variable_highlight = 1
```

Highlighting of class names in declarations is disabled by default. To enable set
```vim
let g:cpp_class_decl_highlight = 1
```

Highlighting of POSIX functions is disabled by default. To enable set
```vim
let g:cpp_posix_standard = 1
```

There are two ways to highlight template functions. Either
```vim
let g:cpp_experimental_simple_template_highlight = 1
```
which works in most cases, but can be a little slow on large files.
Alternatively set
```vim
let g:cpp_experimental_template_highlight = 1
```
which is a faster implementation but has some corner cases where it doesn't
work.

_Note: C++ template syntax is notoriously difficult to parse, so don't expect
this feature to be perfect._

Highlighting of library concepts is enabled by
```vim
let g:cpp_concepts_highlight = 1
```
This will highlight the keywords `concept` and `requires` as well as all named
requirements (like `DefaultConstructible`) in the standard library.

Highlighting of user defined functions can be disabled by
```vim
let g:cpp_no_function_highlight = 1
```

Installation instructions
-------------------------
Follow one of the sets of directions below and reload vim afterwards.

#### Vundle
Install using [vundle](https://github.com/gmarik/Vundle.vim) by adding
```vim
Plugin 'octol/vim-cpp-enhanced-highlight'
```
to .vimrc and run `:PluginInstall`.


#### Git submodule + Pathogen
If you have [pathogen](https://github.com/tpope/vim-pathogen) installed,
and you prefer to use git submodules, run
```sh
cd ~/.vim
git submodule add https://github.com/octol/vim-cpp-enhanced-highlight.git bundle/syntax/
```

#### Manual installation
If you don't have either Vundle or Pathogen installed, copy the cpp.vim file
(optionally also c.vim) to .vim/after/syntax.
```sh
git clone https://github.com/octol/vim-cpp-enhanced-highlight.git /tmp/vim-cpp-enhanced-highlight
mkdir -p ~/.vim/after/syntax/
mv /tmp/vim-cpp-enhanced-highlight/after/syntax/cpp.vim ~/.vim/after/syntax/cpp.vim
rm -rf /tmp/vim-cpp-enhanced-highlight
```

Issues
------

Vim tend to a have issues with flagging braces as errors, see for example
https://github.com/vim-jp/vim-cpp/issues/16. A workaround is to set
```vim
let c_no_curly_error=1
```

Background information
----------------------

- http://stackoverflow.com/questions/736701/class-function-names-highlighting-in-vim
- http://www.vim.org/scripts/script.php?script_id=4293
- http://www.vim.org/scripts/script.php?script_id=2224
- http://www.vim.org/scripts/script.php?script_id=1640
- http://www.vim.org/scripts/script.php?script_id=3064

Jon Haggblad <jon@haeggblad.com>

Last update: 19 October 2016

