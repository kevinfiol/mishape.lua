# mishape.lua

A property validator for associative array/hash-like tables. A port of [https://github.com/kevinfiol/mishape](mishape) to Lua.

```lua
local mishape = require 'mishape'

local Sword = mishape({
    name = 'string',
    damage = 'string|number',
    attributes = {
        strength = 'number',
        range = function (x, is)
            return is.number(x) and x > 1 and x < 5
        end
    }
})

Sword({
    name = 'excalibur',
    damage = 12,
    attributes = {
        strength = 5,
        range = 6
    }
})

-- { ok = false, errors = { 'Expected range, got: 6 at attributes.range' } }
```

## Usage

Drop `mishape.lua` into your existing project and require it:

```lua
local mishape = require 'mishape'
```