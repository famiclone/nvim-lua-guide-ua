# Початок роботи з Lua в Neovim

## Інші переклади

- [:uk: English version](https://github.com/nanotee/nvim-lua-guide)
- [:cn: Chinese version](https://github.com/glepnir/nvim-lua-guide-zh)
- [:es: Spanish version](https://github.com/RicardoRien/nvim-lua-guide/blob/master/README.esp.md)
- [:brazil: Portuguese version](https://github.com/npxbr/nvim-lua-guide/blob/master/README.pt-br.md)
- [:jp: Japanese version](https://github.com/willelz/nvim-lua-guide-ja/blob/master/README.ja.md)
- [:ru: Russian version](https://github.com/kuator/nvim-lua-guide-ru)

## Зміст

- [Початок](#початок)
  - [Вивчення Lua](#вивчення-lua)
  - [Існуючі туторіали](#існуючі-туторіали-по-написанню-lua-в-neovim)
  - [Допоміжні плагіни](#допоміжні-плагіни)
- [Куди класти Lua файли](#куди-класти-lua-файли)
  - [init.lua](#init.lua)

## Початок

[Інтеграція Lua](https://www.youtube.com/watch?v=IP3J56sKtn0) в якості [першокласної мови всередині Neovim](https://github.com/neovim/neovim/wiki/FAQ#why-embed-lua-instead-of-x) перетворює її в одну із найважливіших особливостей. Тим не менш, кількість учбових матеріалів по розробці плагінів на Lua значно менше ніж аналогічних матеріалів на Vimscript. Цей довідник спроба надати базову інформацію для початку.

> Довідник написаний з припущенням, що ви використовуєте що найменш 0.5 версію Neovim.

### Вивчення Lua

Якщо ви ще не знайомі з цією мовою програмування, є велике різноманіття ресурсів щоб почати:

- [Learn X in Y minutes page about Lua](https://learnxinyminutes.com/docs/lua/) надасть вам швидкий огляд основи мови
- [Цей гайд](https://github.com/medwatt/Notes/blob/main/Lua/Lua_Quick_Guide.ipynb) також добрий ресурс для швидкого початку
- Якщо вам більше подобаються відео, [1-hour tutorial on the language](https://www.youtube.com/watch?v=iMacxZQMPXs)
- Потрібно більше інтерактивних прикладів? Спробуй [the LuaScript tutorial](https://www.luascript.dev/learn)
- [Lua-users wiki](http://lua-users.org/wiki/LuaDirectory) великий обсяг корисної інформації по Lua
- [Official reference manual for Lua](https://www.lua.org/manual/5.1/) може дати тобі найкомплексний огляд мови (Є Vimdoc плагін для читання всередині Neovim: [milisims/nvim-luaref](https://github.com/milisims/nvim-luaref))

Слід зазначити що Lua дуже проста мова програмування. Її легко вчити, особливо якщо ви маєте досвід зі схожими мовами - наприклад Javscript. Ви можете знати Lua більше ніж вважаєте!

> Інтегрована версія Lua у Neovim [LuaJIT](https://staff.fnwi.uva.nl/h.vandermeer/docs/lua/luajit/luajit_intro.html) 2.1.0, що підтримує сумісність з Lua 5.1.

### Існуючі туторіали по написанню Lua в Neovim

Декілька туторіалів вже написані щоб допомогти розроблювати Lua плагіни для Neovim. Деякі з них трохи допомогли написати цей довідник. Велика вдячність авторам.

- [teukka.tech - From init.vim to init.lua](https://teukka.tech/luanvim.html)
- [dev.to - How to write neovim plugins in Lua](https://dev.to/2nit/how-to-write-neovim-plugins-in-lua-5cca)
- [dev.to - How to make UI for neovim plugins in Lua](https://dev.to/2nit/how-to-make-ui-for-neovim-plugins-in-lua-3b6e)
- [ms-jpq - Neovim Async Tutorial](https://github.com/ms-jpq/neovim-async-tutorial)
- [oroques.dev - Neovim 0.5 features and the switch to init.lua](https://oroques.dev/notes/neovim-init/)
- [Building A Vim Statusline from Scratch - jdhao's blog](https://jdhao.github.io/2019/11/03/vim_custom_statusline/)
- [Configuring Neovim using Lua](https://icyphox.sh/blog/nvim-lua/)
- [Devlog | Everything you need to know to configure neovim using lua](https://vonheikemen.github.io/devlog/tools/configuring-neovim-using-lua/)

### Допоміжні плагіни

- [Vimpeccable](https://github.com/svermeulen/vimpeccable) - Допоміжний плагін для написання `.vimrc` на Lua
- [plenary.nvim](https://github.com/nvim-lua/plenary.nvim) - Плагін, щоб не писати всі функції Lua двічі
- [popup.nvim](https://github.com/nvim-lua/popup.nvim) - Імплементація Popup API з vim
- [nvim_utils](https://github.com/norcalli/nvim_utils) - Допоміжні утіліти
- [nvim-luadev](https://github.com/bfredl/nvim-luadev) - REPL/дебаг консоль для розробки Lua плагінів
- [nvim-luapad](https://github.com/rafcamlet/nvim-luapad) - Інтерактивна пісочниця для вбудованого Lua
- [nlua.nvim](https://github.com/tjdevries/nlua.nvim) - Lua розробка для Neovim
- [BetterLua.vim](https://github.com/euclidianAce/BetterLua.vim) - Краще підсвічування синтаксису Lua у Vim/NeoVim

## Куди класти Lua файли

### init.lua

Neovim підтримує здатність використовувати конфіги написані на Lua - `init.lua`, окрім звичного `init.vim`

> `init.lua` звісно _опціональний_ формат для конфігурації. Тобто ви можете використовувати звичайний файл конфігурації на _Vimscript_
