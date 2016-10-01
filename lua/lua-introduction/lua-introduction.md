
Lua 
=== 
![Lua-logo-nolabel.png](lua.png)
### Introduction to Lua programming language
<small> By Soulaymen Chouri 
[http://github.com/praisethemoon](http://github.com/praisethemoon)

---

# :heart: Lua is

1. Scripting language
2. Dynamic language
3. Moon in ProtoguÃ©s 
4. Written in ANSI C
5. Highly portable
6. Extremely Fast
7. Open Source

---

# :anger: Lua is not 

- Complete full featured programming language Language
- Game Engine
- IDE

---

# Lua can be used as
:arrow_right: Standalone language
:arrow_right: Static Library
:arrow_right: Shared Object

---

# Hello, world
```lua
print("hello, world")
```

##### Run with
```sh
$ lua ./hello_world.lua
```

---

:heart: .. Simple!
===

---

# Comments

```lua
-- A single line comment :D

--[[
   A multi-line comment
]]
```

---

# Variables

:arrow_right: Default variable scope is **global** unless stated otherwise with `local` keyword

```lua
-- this is a global variable
x = 350 
-- how about a local one
local y = "hello, world"
```

---

# Basic data types

- Lua has **4** basic data types
```lua
-- 1. Numbers: there is no difference between int and float :)
local x = 30
local z = 15.2

-- 2. Booleans
local z, w = true, false
print(z) -- true
print(w) -- false

-- 3. nil
local alpha = nil

-- 4. String
local str = "praise the moon!"
--[[ String concatenation: ]]
local str2 = str .. ", JUST.. DO IT !"
```

---

# For loops

### :arrow_right: Standard loop
```lua
for index = 1, 5 do
	print(index)
end

```

### :arrow_left: Backward loop
```lua
for index = 10, 1, -1 do
    print( index )
end
```

--- 

# While loops
```lua
local keep = true
local x = 10

while keep do
	x = x - 1
	if x < 5 then 
		keep = false
	end
end
```

---

# Repeat loops

```lua
local x = 0

repeat 
	x = x + 20
until x > 100

```

---

# Lua has no `continue` statement :-1:

---

# Complex data types
Use `type` to get any variable type

```lua
local x = 15

print(type(x))
--  prints "number"

print(type("whale hello there"))
--  prints "string"

print(type(nil))
--  prints "nil"
```

---

# Functions

```lua
function abs(x)
	if x > 0 then
		return x
	end
    
	return -x
end

-- function can return more than one value
function foo(x, y)
	return x+1, y+1
end

local x, y = 10, 45
x, y = foo(x, y)
```

--- 

# Functions

#### :heart: First class functions
:arrow_right: Functions can be passed as parameters, returned by other functionss, etc.

---

## Example 

```lua
local oldprint = print

function print(s)     
	if s == "foo" then
		oldprint("bar")
	else
		oldprint(s)
	end
end

--- Functions 
```

---

## Another example
```lua
function addto(x)
	return function(y)
		-- a closure!
		return x + y
	end
end

fourplus = addto ( 4 )
print(type(fourplus)) -- prints "function"
print ( fourplus ( 3 ) )  -- prints 7
```

--- 

# Tables

## `table = { key = value }`

---

# Tables

```lua
-- empty table
a_table = { }

a_table = { x = 10 }

print( a_table ["x"] )  
â€“- prints 10

--[[ MORE ]]

b_table = a_table 

b_table["x"] = 20   

print( b_table["x"] ) 
print( a_table.x ) 
â€“- both prints 20
```

:arrow_right: Tables are passed by reference!

---

# Tables 
## Tables as namespaces

```lua
Point = { } 

-- Different syntax, but just a function declaration
Point.new = function(x, y)
	return{x = x, y = y}
end

function Point.set_x(point, x)
	point.x = x
end

local p1 = Point.new(30, 20)

Point.set_x(p1, 10)
```

---

# Tables 
## Tables as Arrays

:arrow_right: Lua arrays are **1-indexed**

```
array = { "a", "b", "c", "d" }
print(array[2]) -- prints b

array[0] = "z" 
--[[ illegal ]]

-- array size operator:
print(#array) 
-- prints 4
```

--- 

# Iterating through tables

:arrow_right:  Tablse have the form of `{ key = value }`

```lua
local t = {"hello", "world", "son"}
for i, v in ipairs(t) do
	-- i is the key
	-- v is the value
	print(i, v)
end
```
#### Outputs
```lua
1       hello
2       world
3       son
```

---

# Iterating through tables

:arrow_right: You can ignore one of them using `_` :

```lua
for _, v in ipairs(t) do
	print(i, v)
end
```

---

# Iterating through tables

```lua
for i = 1, #t do
	print(i, v)
end
```

---

# Other data types
- `usertype`
- `thread`

:arrow_right: Not discussed here

---

# Creating a library

:arrow_right:  Always localize variables to optimize **performance** and **thread safety**

:arrow_right: Encapsulate your library in a namespace and return it.

```lua
-- awesome.lua
-- my awesome library
local awesome = {}

awesome.bar = "praise the moon!"

function awesome.foo() 
	print("hello, awesome!")
end

return awesome
```

---

# Using your library :sunglasses:
```
local awesome = require 'awesome'

print(awesome.bar)

awesome.foo()
```

---

# Notes:

- Any global variable/function within your module will be visible to any source file importing it
- Localizing and returning an entire package is a good habbit.

---

# Meta-tables
:arrow_right: A very strong features allowing the programmer to override the some behaviours of a variable.
:arrow_right: Can be only applied to tables

---


### Example
We want to add two vectors:

```
local v = {x = -30, y = 10}

local mt = {
	__add = function (lhs, rhs) 
		return { x = lhs.x + rhs.x, y = lhs.y + rhs.y }
	end
}

setmetatable(v, mt) 

-- Using it 
local w = {x = 50, y = 15}

local z = v + w
-- this will trigger the __add method of the meta-table assigned to v

print(z.x  .. ", " .. z.y)
-- prints "20, 25"
```

--- 

# Where to go from here:
- Lua manual: [https://www.lua.org/manual/5.1/manual.html](https://www.lua.org/manual/5.1/manual.html)
- Lua tutorial:  [https://www.tutorialspoint.com/lua/index.htm](https://www.tutorialspoint.com/lua/index.htm)
- Lua Users Wiki :heart:: [http://lua-users.org/wiki/LuaDirectory](http://lua-users.org/wiki/LuaDirectory) 

---

:heart: Thank you 
===