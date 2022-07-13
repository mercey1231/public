## Concat2Argument

### Instructions

Write a program that concatenates two arguments  and prints the result:
- If the number of arguments is not 2, return newline.
- If the two arguments are empty return newline.  

### Usage

```console
$ go run . | cat -e
$
$ go run . "Hello" "World!" | cat -e
HelloWorld!$
$ go run . " student " talented | cat -e
 student talented$
$ go run . "Hello" "student" talented ! | cat -e
$
``` 