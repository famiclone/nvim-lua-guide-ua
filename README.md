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
  - [init.lua](#initlua)
  - [Модулі](#модулі)
    - [Поради](#поради)
  - [Файли рантайму](#файли-рантайму)
    - [Поради](#поради)
- [Використання Lua у Vimscript](#використання-lua-у-vimscript)
  - [:lua](#lua)
  - [:luado](#luado)
  - [Підключення Lua файлів](#підключення-lua-файлів)
    - [Різниця між підключенням та викликом require()](#різниця-між-підключенням-та-викликом-require)
  - [luaeval()](#luaeval)
  - [v:lua](#vlua)
    - [Застереження](#застереження)
  - [Поради](#поради)
- [Простір імен vim](#простір-імен-vim)
  - [Поради](#поради)

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

> `init.lua` звісно **опціональний** формат для конфігурації. Підтримка `init.vim` не зникла, та може використовуватись разом з Lua-конфігом. Також поки що не всі функції редактора підтримуються через Lua.

Дивіться також:

- [`:help config`](https://neovim.io/doc/user/starting.html#config)

### Модулі

Lua модулі можна знайти всередині `lua/` директорії в вашому `'runtimepath'` (для більшості юзерів це буде `~/.config/nvim/lua` на \*nix системах та `~/AppData/Local/nvim/lua` на Windows. За допомогою функції `require()` ви можете імпортити модулі з ціеї директорії.

Давайте розглянемо структуру директорій:

```text
📂 ~/.config/nvim
├── 📁 after
├── 📁 ftplugin
├── 📂 lua
│  ├── 🌑 myluamodule.lua
│  └── 📂 other_modules
│     ├── 🌑 anothermodule.lua
│     └── 🌑 init.lua
├── 📁 pack
├── 📁 plugin
├── 📁 syntax
└── 🇻 init.vim
```

Наступний код завантажить `myluamodule.lua`:

```lua
require('myluamodule')
```

Можете не вказувати розширення `.lua`.
Схожим чином завантаження `other_modules/anothermodule.lua` виглядає так:

```lua
require('other_modules.anothermodule')
```

або

```lua
require('other_modules/anothermodule')
```

Розділителі шляху можуть бути крапкою `.` або слешем `/`.

Якщо ви намагаєтесь завантажити не існуючий модуль, це призведе до помилки та відміни виконання скрипта.
`pcall()` функція може бути використана для запобігання помилок.

```lua
local ok, _ = pcall(require, 'module_with_error')
if not ok then
  -- не заванжувати
end
```

Дивіться також:

- [`:help lua-require`](https://neovim.io/doc/user/lua.html#lua-require)

#### Поради

Деякі плагіни можуть мати однакові імена файлів у `lua/` директорії. Це може призвести до конфлікту простору імен.

Якщо два різних плагіни мають файл `lua/main.lua`, а потім завантажуються шляхом `require('main')`, то який з них буде використаний?

Тому буде гарною ідеєю покласти кожен `main.lua` файл у діректорію з назвою плагіну: `lua/plugin_name/main.lua`

### Файли рантайму

Як і Vimscript файли, Lua файли можуть бути завантажені автоматично зі спеціальної директорії `runtimepath`. На даний час підтримуються наступні назви директорій:

- `colors/`
- `compiler/`
- `ftplugin/`
- `ftdetect/`
- `indent/`
- `plugin/`
- `syntax/`

> У рантайм директорії, усі `*.vim` файли мають бути визвані після `*.lua` файлів.

Дивіться також:

- [`:help 'runtimepath'`](https://neovim.io/doc/user/options.html#'runtimepath')
- [`:help load-plugins`](https://neovim.io/doc/user/starting.html#load-plugins)

#### Поради

Поки файли рантайму не базуються на системі модулів Lua, два плагіни можуть мати файл `plugin/main.lua` без проблем.

## Використання Lua у Vimscript

### :lua

Ця команда виконує шматок Lua коду.

```lua
:lua require('myluamodule')
```

За допомогою heredoc синтаксису можливо виконувати багаторядкові скріпти:

```vim
echo "Here's a bigger chunk of Lua code"

lua << EOF
local mod = require('mymodule')
local tbl = {1, 2, 3}

for k, v in ipairs(tbl) do
    mod.method(v)
end

print(tbl)
EOF
```

> Кожна `lua` команда має свою область бачення та змінні оголошені з ключовим словом `local` не будуть доступні за межами команди. Приклад:

```vim
:lua local foo = 1
:lua print(foo)
" виведе 'nil' замість '1'
```

> Lua функція `print()` поводиться схоже до `:echomsg` команди. Вихідні дані будуть збережені у історіі повідомлень.

Дивіться також:

- [`:help :lua`](https://neovim.io/doc/user/lua.html#Lua)
- [`:help :lua-heredoc`](https://neovim.io/doc/user/lua.html#:lua-heredoc)

### :luado

Ця команда виконує шматок Lua коду який діє на діапазон рядків у поточному буфері. Якщо рядки не зазначені, то для цілого буферу. Будь-який рядок який повернувся з блоку, використовується для визначення того, чим слід замінити кожен рядок.

Наступна команда замінила би кожен рядок у поточному буфері текстом `hello world`:

```vim
:luado return 'hello world'
```

Дві неявні змінні `line` та `linenr` також доступні. `line` – це текст рядка, а `linenr` – номер. Наступна команда зробить кожен рядок у верхньому регістрі, якщо номер рядка ділиться на 2 без залишку:

```vim
:luado if linenr % 2 == 0 then return line:upper() end
```

Дивіться також:

- [`:help :luado`](https://neovim.io/doc/user/lua.html#:luado)

### Підключення Lua файлів

Neovim надає 3 Ex команди щоб підключити Lua файли:

- `:luafile`
- `:source`
- `:runtime`

`:luafile` та `:source` дуже схожі:

```vim
:luafile ~/foo/bar/baz/myluafile.lua
:luafile %
:source ~/foo/bar/baz/myluafile.lua
:source %
```

`:source` також підтримує діапазони, котрі будуть корисні для виконання частини скрипту:

```vim
:1,10source
```

Команда `runtime` дещо відрізняється: вона використовує `'runtimepath'` опцію для визначення директорії звідки будуть підключені файли. Більшe деталей: [`:help :runtime`](https://neovim.io/doc/user/repeat.html#:runtime).

Дивіться також:

- [`:help :luafile`](https://neovim.io/doc/user/lua.html#:luafile)
- [`:help :source`](https://neovim.io/doc/user/repeat.html#:source)
- [`:help :runtime`](https://neovim.io/doc/user/repeat.html#:runtime)

#### Різниця між підключенням та викликом require():

Можливо вам цікаво у чому різниця та чи варто віддавати перевагу одному способу над іншим. Вони мають різні випадки використання:

- `require()`:
  - вбудована функція Lua. Дозволяє користуватися перевагами модульної системи Lua
  - шукає модулі у директорії `lua/` у вашому `'runtimepath'`
  - дозволяє слідкувати за тим які модулі були завантажені та запобігає повторному парсингу та виконанню скрипта. Якщо ви зміните код у вже завантаженому модулі та спробуєте завантажити його через `require()` ще раз, то зміни не застосуються.
- `:luafile`, `:source`, `:runtime`:
  - Ex команди. Не підтримують модулі
  - повторно виконують раніше виконані скрипти
  - `:luafile` та `:source` приймають шлях до файлу як абсолютний так і відносний до робочої директорії поточного вікна
  - `:runtime` використовує `'runtimepath'` опцію щоб знайти файли

### luaeval()

Ця вбудована Vimscript функція виконує Lua вираження та повертає результат. Типи данних Lua автоматично конвертуються у Vimscript типи (і навпаки).

```vim
" You can store the result in a variable
let variable = luaeval('1 + 1')
echo variable
" 2
let concat = luaeval('"Lua".." is ".."awesome"')
echo concat
" 'Lua is awesome'

" List-like tables are converted to Vim lists
let list = luaeval('{1, 2, 3, 4}')
echo list[0]
" 1
echo list[1]
" 2
" Note that unlike Lua tables, Vim lists are 0-indexed

" Dict-like tables are converted to Vim dictionaries
let dict = luaeval('{foo = "bar", baz = "qux"}')
echo dict.foo
" 'bar'

" Same thing for booleans and nil
echo luaeval('true')
" v:true
echo luaeval('nil')
" v:null

" You can create Vimscript aliases for Lua functions
let LuaMathPow = luaeval('math.pow')
echo LuaMathPow(2, 2)
" 4
let LuaModuleFunction = luaeval('require("mymodule").myfunction')
call LuaModuleFunction()

" It is also possible to pass Lua functions as values to Vim functions
lua X = function(k, v) return string.format("%s:%s", k, v) end
```

`luaeval()` приймає опціональний другий аргумент який дозволяє передавати дані до вираження. Потім у вас буде доступ до данних через магічну глобальну змінну `_A`:

```vim
echo luaeval('_A[1] + _A[2]', [1, 1])
" 2

echo luaeval('string.format("Lua is %s", _A)', 'awesome')
" 'Lua is awesome'
```

Дивіться також:

- [`:help luaeval()`](<https://neovim.io/doc/user/lua.html#luaeval()>)

### v:lua

Це глобальна Vim змінна дозволяє вам викликати Lua функції у глобальному просторі імен ([`_G`](https://www.lua.org/manual/5.1/manual.html#pdf-_G)) напряму з Vimscript. І знову типи данних Vim будуть сконвертовані у Lua типи і навпаки.

```vim
call v:lua.print('Hello from Lua!')
" 'Hello from Lua!'

let scream = v:lua.string.rep('A', 10)
echo scream
" 'AAAAAAAAAA'

" How about a nice statusline?
lua << EOF

" How about a nice statusline?
lua << EOF
function _G.statusline()
    local filepath = '%f'
    local align_section = '%='
    local percentage_through_file = '%p%%'
    return string.format(
        '%s%s%s',
        filepath,
        align_section,
        percentage_through_file
    )
end
EOF

set statusline=%!v:lua.statusline()

" Also works in expression mappings
lua << EOF
function _G.check_back_space()
    local col = vim.api.nvim_win_get_cursor(0)[2]
    return (col == 0 or vim.api.nvim_get_current_line():sub(col, col):match('%s')) and true
end
EOF

inoremap <silent> <expr> <Tab>
    \ pumvisible() ? "\<C-N>" :
    \ v:lua.check_back_space() ? "\<Tab>" :
    \ completion#trigger_completion()

" Call a function from a Lua module by using single quotes and omitting parentheses:
call v:lua.require'module'.foo()
```

Дивіться також:

- [`:help v:lua`](https://neovim.io/doc/user/eval.html#v:lua)
- [`:help v:lua-call`](https://neovim.io/doc/user/lua.html#v:lua-call)

#### Застереження

Ця змінна може бути використана тільки для виклику функцій. Наступний код завжди буде викидувати помилку:

```vim
" Aliasing functions doesn't work
let LuaPrint = v:lua.print

" Accessing dictionaries doesn't work
echo v:lua.some_global_dict['key']

" Using a function as a value doesn't work
echo map([1, 2, 3], v:lua.global_callback)
```

### Поради

Ви можете увімкнути підсвічення синтаксису Lua всередині `.vim` файлів. Додайте `let g:vimsyn_embed = 'l'` до вашого файлу конфігурації. Більше інформаціЇ [`:help g:vimsyn_embed`](https://neovim.io/doc/user/syntax.html#g:vimsyn_embed).

## Простір імен vim

Neovim має глобальну змінну `vim` яка є вхідною точкою до API з Lua коду. Це надає користувачам розширену стандартну бібліотеку функцій, а також різноманітні підмодулі.

Деякі важливі функції та модулі:

- `vim.inspect`: трансформує Lua обʼєкти до людино-зрозумілий вигляду (корисно для інспектування Lua таблиць)
- `vim.regex`: використовуйте регулярні вираження vim із Lua
- `vim.api`: модуль який надає доступ до API функцій (також використовується віддаленими плагінами)
- `vim.ui`: UI функції
- `vim.loop`: модуль для доступу до event-loop (використовує LibUV)
- `vim.lsp`: модуль що контролює вбудований LSP клієнт
- `vim.treesitter`: модуль для доступу до функціоналу бібліотеки tree-sitter

Цей список не є вичерпним. Якщо ви бажаєте знати що доступно через `vim` змінну, [`:help lua-stdlib`](https://neovim.io/doc/user/lua.html#lua-stdlib) та [`:help lua-vim`](https://neovim.io/doc/user/lua.html#lua-vim). Додатково, ви можете використовувати команду `:lua print(vim.inspect(vim))` щоб отримати повний список модулів. API функції теж документовані [`:help api-global`](https://neovim.io/doc/user/api.html#api-global).

#### Поради

Писати `print(vim.inspect(x))` кожен раз коли треба проінспектувати вміст обʼєкта може бути нудним процесом. Можливо, варто мати глобальну обгортку десь у файлі конфігурації (у Neovim 0.7.9+, ця функція вбудована, більше інформації [`:help vim.pretty_print()`](<https://neovim.io/doc/user/lua.html#vim.pretty_print()>)):

```lua
function _G.put(...)
  local objects = {}
  for i = 1, select('#', ...) do
    local v = select(i, ...)
    table.insert(objects, vim.inspect(v))
  end

  print(table.concat(objects, '\n'))
  return ...
end
```

You can then inspect the contents of an object very quickly in your code or from the command-line:
Тепер ви можете інспектувати вміст обʼєкту швидко у вашому коді чи через командний рядок:

```lua
put({1, 2, 3})
```

```vim
:lua put(vim.loop)
```

Додатково ви можете використовувати `:lua` команду для красиво вивести вираження додавши до нього префікс `=` (Neovim 0.7+)

```vim
:lua =vim.loop
```
