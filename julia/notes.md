*based on [julia tutorial][1]*
*created on: 2022-10-14 17:28:24*

## Julia Tutorial

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



[//]: <> (References)
[1]: <https://juliaacademy.com/courses/enrolled/375479>

[//]: # (Some snippets)
[//]: # (add an image <img src="" style='height:400px;'>)
