<div align="center">
    <img href="https://projecterror.dev" width="150" src="https://i.tasoagc.dev/c1pD" alt="Material-UI logo" />
</div>
<h1 align="center">FiveM Style Guide for Lua</h1>

<div align="center">
<em>
A mostly reasonable style & convention guide for FiveM's Lua ScRT
</em>
</div>

<div align="center">

[![license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/project-error/pe-utils/master/LICENSE)
![Discord](https://img.shields.io/discord/791854454760013827?label=Our%20Discord)
</div>

## Intro
Unlike a language like JavaScript, Lua does not have a widely accepted styling across
implementations. This style guide aims to ensure that styling is consistent across all
Project Error Lua files.

Much of this style guide is based off popular JS/TS conventions.

## Identation
I.1 - Always use `spaces` as target indentation
> Primarily for code readability on GitHub as tabs are displayed as 8 spaces by default

I.2 - Use two spaces for indent spacing
> Opionated carryover from JS/TS conventions.

## Events & Exports
E.1 - Non-net cross resource communication should use exports
> Why? Although exports are simple wrappers around events, they offer
> caching.

E.2 - NetEventHandlers on the Server should use `RegisterServerEvent`
> Under the hood this is an alias to `RegisterNetEvent`. `RegisterServerEvent`
> is preferred for easy identification of Server Side handlers. (i.e Searching through
> a resource)

E.3 - Always use the optional callback argument for RegisterNetEvent
> Increased readability and more concise
```lua
-- Good
RegisterNetEvent('netEvent', handlerFunc)

-- Bad
RegisterNetEvent('netEvent')
AddEventHandler('netEvent', handlerFunc)
```

## Casing
C.1 - Constants should use upper case snakecase
```lua
-- Good
local INTERVAL_TIME = 50

-- Bad
local intervalTime = 50
```

C.2 - Local variables or functions should use camelCase
```lua
local myVar = {}

local function myLocalFunction()  end
```

C.3 - Global variables or functions should use upper camelcase
```lua
MyGlobalVar = 'nice'

function MyGlobalFunction()  end
```

## Misc
M.1 - Where possible, avoid using the Citizen prefix for the `Citizen` table of functions
> The most commonly used citizen table functions are aliased to work with removing the prefix. This
> appears more concise.
```lua
-- Bad
Citizen.CreateThread(fn)

-- Good
CreateThread(fn)
```
> List of aliased functions:
```lua
SetTimeout
Wait
CreateThread
RconPrint -- Citizen.Trace
```
