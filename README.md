# Початок роботи з Lua в Neovim

## Інші переклади

- [:en: English version](https://github.com/nanotee/nvim-lua-guide)
- [:cn: Chinese version](https://github.com/glepnir/nvim-lua-guide-zh)
- [:es: Spanish version](https://github.com/RicardoRien/nvim-lua-guide/blob/master/README.esp.md)
- [:brazil: Portuguese version](https://github.com/npxbr/nvim-lua-guide/blob/master/README.pt-br.md)
- [:jp: Japanese version](https://github.com/willelz/nvim-lua-guide-ja/blob/master/README.ja.md)
- [:ru: Russian version](https://github.com/kuator/nvim-lua-guide-ru)

## Зміст

* [Початок](#початок)
  * [Вивчення Lua](#вивчення-lua)

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
