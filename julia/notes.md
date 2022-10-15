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







[//]: <> (References)
[1]: <https://juliaacademy.com/courses/enrolled/375479>

[//]: # (Some snippets)
[//]: # (add an image <img src="" style='height:400px;'>)
