# Component Architecture

## Brief Summary
- Component
- Reference Counting
- Interface

## Statement-Interface Interop
- `for each`: `ifEnum` (`Array`,`Associative Array`,`ByteArray`,`MessagePort`)
- `print`: `ifEnum`,`ifString`,`ifInt`,`ifFloat`
- `wait`: `ifMessagePort`
- `[]`: `ifArrayGet`, `ifArraySet` (`Array`,`Associative Array`,`ByteArray`,`List`)
- `.` : `ifAssociativeArray` (but also on all BrightScript Components)

## Intrinsic Types
- `Integer`, `Float`, `Double`, `String`, `Invalid`, `Boolean`, `Function`
- value types

## Object Types
- `Array`, `Associative Array`, `BrightScript Component`
- reference types

## Boxing

```py
foo(4)

function foo(i as Object) as Void
  ? type(i) ' roInt
end function
```

## BrightScript XML Support

## Garbage Collection
- instantaneous for ref-count zero strings and objects
- delayed for circular references
  - invocable by `RunGarbageCollector()`
 
## Events
```py
fs = CreateObject("roFilesystem")
port = CreateObject("roMessagePort")
fs.SetMessagePort(port)
while true
    msg = wait(0, port)
    if type(msg)="roFileSystemEvent" then
        if msg.isStorageDeviceAdded() then print "device added"
    end if
End While
```

## Threading Model
- Script runs ina single thread
- A program cannot create multiple threads
- function calls are asynchronous if they take long
  - e.g. `roVideoPlayer.Play()`

## Scope
- No global variables
  - One `global` BrightScript Component
  - One `GetGlobalAA()` Context
- `function`s are global scope unless anonymous
- Local variables and labels exist in function scope
- block statements do not create a scope

## Intrinsic Objects
- object refers to "BrightScript Component"
  - C/C++ components with interfaces and member functions
- you can also create intrinsic objects
  - similar to components
  - but do not support interfaces
- `roAssociativeArray` which contains function references
  - `m` is a special pointer refering to the associative array
  - `constructor` is a normal function at global scope that creates and returns the AA
 
## This Pointer

```py
function ConstructObject()
  obj = {
    Set : function(x) : m.Value = x : end function
    Get : function() : return m.Value : end function
    Value : 0
  }
  return obj
end function
```

##  Script Libraries
- common libraries under `common:/LibCore`

### Example: Library "v30/bslCore.brs"
Can be seen from the Debug Console:
```bash
BrightScript> bslCore =
ReadAsciiFile("common:/LibCore/v30/bslCore.brs")  
BrightScript> print bslCore
```
