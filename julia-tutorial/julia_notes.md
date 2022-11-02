*based on [julia tutorial][1]*
*created on: 2022-10-14 17:28:24*

## Julia Tutorial

```julia 
# this is a line comment 
#=
this is a multi 
line 
comment  
=#
```

you can use `convert()` to change the type of variable 

```julia
days =365 
days_float = convert(Float64, days)
```
and to cast you can use `parse()`

```julia
parse(Int64, "1") 
```
### Strings 

Single quotation marks `''` are exclusively use for `chars` therefore can only encapsulate one `char`. For a general string use `"some text"` and if you need to encapsulate quotation marks inside a string you can use the triple quotation mark `""" "oh" said x """`

To insert variables inside text we can use `$` to call some variable names

```julia
name = "Jane"
println("Hello, my name is $name.")
```
you can also operate inside the strings 

```julia
num_fingers = 10
num_toes = 10
println("That is $(num_fingers + num_toes) digits in all!!")
```
to concatenate strings you can use the `string()` function, but also the `*` operator, or use string formatting 

```julia
string(s3, s4)
s3*s4
"$s3*$s4"
```

### data structures 

to declare a dictionary we use 
```julia 
myphonebook = Dict("Jenny" => "867-5309", "Ghostbusters" => "555-2368")
myphonebook["Kramer"] = "555-FILK" # to add a new key just use the brackets 
pop!(myphonebook, "Kramer") # this will get the value in key and remove it from the dictionary 
```

to declare tuples we use the following syntax. **The indexing started at 1**. we can't edit tuples because they are **immutable** 

```julia 
myfavoriteanimals = ("penguins", "cats", "sugargliders")
myfavoriteanimals[1] # print penguins, the indexes started at 1 !!

# we can also create named tuples using key pairs 
myfavoriteanimals = (bird = "penguins", mammal = "cats", marsupial = "sugargliders")
myfavoriteanimals.bird #  and we can key/property get the data 
```

to declare `arrays` we use the square brackets 
```julia 
myfriends = ["Ted", "Robyn", "Barney", "Lily", "Marshall"]
mixture = [1, 1, 2, 3, "Ted", "Robyn"]
#arrays are mutable 
mixture[1] = 0 # and the indexing started at 1
```
We can use the `push!()` function to `list.append()` an element. (`pop!` same as `pop()`).
We can use the `rand(i,j,k)` function to create a random matrix with `i,j,k `dimensions 

### Loops 

we can use a `while` loop to iterate over an array. The loop block is defined by the `end` keyword

```julia 
myfriends = ["Ted", "Robyn", "Barney", "Lily", "Marshall"]
i = 1 # the array index started at 1 
while i <= length(myfriends) # no, so we use the `end`
    friend = myfriends[i] # the indentation is not necessary 
    println("Hi $friend, it's great to see you!")
    i += 1 # increment equal to python 
end # we finish the block using an end keyword 
```

to use the `for` loop we can use different syntaxes 
```julia 
for n in 1:10 # how to define a range
    println(n)
end

# using an iterable such as an array 
myfriends = ["Ted", "Robyn", "Barney", "Lily", "Marshall"]

for friend in myfriends # we can use `in` or `\in` or `=` 
    println("Hi $friend, it's great to see you!")
end

#to iterate over a matrix we can use a nested for loop in one line `it.combination`

B = fill(0, (m, n)) # generate a zeroes matrix of m,n
for j in 1:n, i in 1:m  # iterate over n,m 
    B[i, j] = i + j
end
# there is also a way to do two loops inside a list comprehension 
C = [i + j for i in 1:m, j in 1:n] # this will create a matrix with m,n
```
### Conditionals 

to write a conditional if we use the same `end` block and the `elseif` (`elif` in python)
```julia
if x > y
    x
elseif y == 1
    y
else 
    print("end condition")
end
# we can also use a ternary operator as in javascript 
(x > y) ? x : y
```

to declare `and` we use `&&` also julia evaluates from right to left, so is more efficient to add the conditions from the less complex to the hardest. `or`  is evaluated using `||` 

```julia 
false && (println("hi"); true) # we can concatenate lines using ; and ()
# concatenate lines using ; and ()
(a = 1; b = 3; print(a+b);)
# using or 
true || println("hi")
```

### Functions 

to declare a function we use the following block. Julia uses ducktyping by default. In the lower example we can use `f(4)`or even `f("somestring")` and it will try to run the code even with that argument.    

```julia 
function f(x)
    x^2
end
# or declare it in one line 
f2(x) = x^2
# we can also declare it as an anonymous function (lambda)
f3 = x -> x^2
```
**In Julia the function returns the last expression evaluated**, to be explicit you can use also the `return` [keyword][6].
```julia 
function f(x::Float)::Number # we declare the type using :: and the return also can be declared at the end 
   return x^2
end

function f(x::Number) # void method 
    print(x)
    return nothing # you can also return nothing (in case this is a void method )
    return # this will also return nothing 
end
```

All operators in Julia are functions (except for `&&` and `||`), therefore they can be applied or map to elements 

```julia 
+(2,2) # 4
+(1,2,3) #6
map(+,[1,2,3]) # 6

A.prop	# getproperty
A.prop = 3 # setproperty!

```


By convention, functions followed by `!` alter their contents and functions lacking `!` do not.
For example, let's look at the difference between `sort` and `sort!`.

```julia 
sort(v) # this will not mutate v and it will return a new vector that is sorted 
sort!(v) # this will mutate v and it will changed to a sorted value 
```

`map(f:function, v:iterable)` is a function that will apply element wise the function `f` to the iterable `v`. `broadcast` will do the same except when there is a different vectors shapes and they have to [infer it][2], you can use `f.(v)` to broadcast `f` on `v`

```julia 
map(f,v) #this will apply f to all elements in V 
broadcast(f,v) # this will do the same 
f.(v) # this will call broadcast(f,v) is just a syntactic sugar 
```

### Packages 
[Julia Packages][3], to search use [JuliaHub][4]. To add a package you call the `Pkg` (package manager -`pip`-) and then use `Pkg.add("name_of_package")`. 

```julia 
using Pkg # load package manager 
Pkg.add("Colors") # add Colors package 
using Colors # load Colors 
palette = distinguishable_colors(100) # you can call all the functions from the namespace exported from colors (a mess!!!!)
# to avoid importing all the functions into the namespace use import 

import Colors
distinguishable_colors() # will not work 
Colors.distinguishable_colors() # will work

# or you can use, to also explicitly call the origin of a function 
import Colors: distinguishable_colors
```

To manage environments Julia uses directory names as the env name and add some list of dependencies, use the REPL to install packages and use the current environment, [more instructions here][5] 

```bash
cd myproject
julia # call REPL 
']' # load package manager 
activate . # activate `myproject` env (this will load the MyProject.toml, and Manifest.toml)
add IJulia # this will install a package in the envirorment 
```

### Multiple Dispatch 

by definition in Julia we can `@overload` the same function name `f` and define different methods that will apply depending on the type of the argument 

```julia 
foo(x::String, y::String) = println("My inputs x and y are both strings!")
foo(x::Int, y::Int) = println("My inputs x and y are both integers!")
```
if we call `foo("a","b")` the first definition will be used, and if we do `foo(2,3)` the second definition will be use, if we do `foo(2.34,23.5)` this will raise an error, duck typing doesn't work when the type of the argument is defined. To duck type always define a "generic" method 

```julia 
methods(foo) # this will print all the possible definitions or methods. 
@which foo(3, 4) # this will show the exact method applied when <int>,<int>
```
we can define more abastract types such as `Number`

```julia
foo(x::Number, y::Number) = println("My inputs x and y are both numbers!")
```

### Struct 
is a way to declare `dataclasses` in `Julia` 

```julia
struct MyObj
    field1
    field2
end 

my_instance = MyObj("hello","world")
my_instance.field1 # this print "hello"
```

by default Structs in Julia are immutable, to declare a mutable one we can use the keyword `mutable`

```julia
mutable struct Person
    name::String # this types are typechecked, not trying to be converted (not ducktyping by default)
    age::float64
end 
```

we can define `classmethods` or constructors defining a function with the same ClassName name 

```julia
mutable struct Person
    name::String 
    age::float64
    
    function Person(name::String) # this is a constructor
        new(name, 20.0) # this.new [cls]
    end
end 
```
### some linear algebra functions 

```julia
A' # \= traspose(A)
A\b # Ax=b, x = A/b
```

### Symbol
In Julia a [`Symbol`][7] will represent a private string in Julia (such as `+` or `=` or `var` where var is a declared variable, or could be a function name, etc). You usually eval and declare `Symbols` using `:` therefore 

```julia 
var = "hola"
:var # this is the symbol for the variable `var`

```
### select 




[//]: <> (References)
[1]: <https://juliaacademy.com/courses/enrolled/375479>
[2]: <https://stackoverflow.com/a/65291051/5318634>
[3]: <https://julialang.org/packages/>
[4]: <https://juliahub.com/ui/Packages>
[5]: <https://pkgdocs.julialang.org/v1/environments/>
[6]: <https://docs.julialang.org/en/v1/manual/functions/#The-return-Keyword>
[7]: <https://stackoverflow.com/a/23482257/5318634>

[//]: # (Some snippets)
[//]: # (add an image <img src="" style='height:400px;'>)
