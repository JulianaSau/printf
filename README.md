# 0x11. C - printf

An ALX collaborative project where we create our own printf function using C

# Resources

## Read or watch:

- Secrets of printf
- Group Projects concept page (Don’t forget to read this)
- Flowcharts concept page

## `man` or `help`:

- `printf (3)`

## Requirements

### General

- Allowed editors: `vi`, `vim`, `emacs`
- All your files will be compiled on `Ubuntu 20.04 LTS` using `gcc`, using the options `-Wall -Werror -Wextra -pedantic -std=gnu89`
- All your files should end with a new line
- A `README.md` file, at the root of the folder of the project is mandatory
- Your code should use the `Betty` style. It will be checked using `betty-style.pl` and `betty-doc.pl`
- You are not allowed to use global variables
- No more than 5 functions per file
- In the following examples, the `main.c` files are shown as examples. You can use them to test your functions, but you don’t have to push them to your repo (if you do we won’t take them into account). We will use our own `main.c` files at compilation. Our `main.c` files might be different from the one shown in the examples
- The prototypes of all your functions should be included in your header file called `main.h`
- Don’t forget to push your header file
- All your header files should be include guarded
- Note that we will not provide the `_putchar` function for this project

## GitHub

There should be one project repository per group. If you clone/fork/whatever a project repository with the same name before the second deadline, you risk a 0% score.

## More Info

### Authorized functions and macros

- `write` (`man 2 write`)
- `malloc` (`man 3 malloc`)
- `free` (`man 3 free`)
- `va_start` (`man 3 va_start`)
- `va_end` (`man 3 va_end`)
- `va_copy` (`man 3 va_copy`)
- `va_arg` (`man 3 va_arg`)

## Compilation

- Your code will be compiled this way:
  `bash $ gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c `
- As a consequence, be careful not to push any `c` file containing a `main` function in the root directory of your project (you could have a test folder containing all your tests files including `main` functions)
- Our main files will include your main header file (`main.h`): `#include main.h`
- You might want to look at the gcc flag -Wno-format when testing with your `_printf` and the standard `printf`. Example of test file that you could use:

  ```bash
  #include <limits.h>
  #include <stdio.h>
  #include "main.h"

  /**
   * main - Entry point
   *
   * Return: Always 0
   */
  int main(void)
  {
      int len;
      int len2;
      unsigned int ui;
      void *addr;

      len = _printf("Let's try to printf a simple sentence.\n");
      len2 = printf("Let's try to printf a simple sentence.\n");
      ui = (unsigned int)INT_MAX + 1024;
      addr = (void *)0x7ffe637541f0;
      _printf("Length:[%d, %i]\n", len, len);
      printf("Length:[%d, %i]\n", len2, len2);
      _printf("Negative:[%d]\n", -762534);
      printf("Negative:[%d]\n", -762534);
      _printf("Unsigned:[%u]\n", ui);
      printf("Unsigned:[%u]\n", ui);
      _printf("Unsigned octal:[%o]\n", ui);
      printf("Unsigned octal:[%o]\n", ui);
      _printf("Unsigned hexadecimal:[%x, %X]\n", ui, ui);
      printf("Unsigned hexadecimal:[%x, %X]\n", ui, ui);
      _printf("Character:[%c]\n", 'H');
      printf("Character:[%c]\n", 'H');
      _printf("String:[%s]\n", "I am a string !");
      printf("String:[%s]\n", "I am a string !");
      _printf("Address:[%p]\n", addr);
      printf("Address:[%p]\n", addr);
      len = _printf("Percent:[%%]\n");
      len2 = printf("Percent:[%%]\n");
      _printf("Len:[%d]\n", len);
      printf("Len:[%d]\n", len2);
      _printf("Unknown:[%r]\n");
      printf("Unknown:[%r]\n");
      return (0);
  }
  ```

- How to run the test:

  ```bash
  gcc -Wall -Wextra -Werror -pedantic -std=gnu89 -Wno-format *.c && ./printf
  ```

- Example response is:
  ```bash
  Let's try to printf a simple sentence.
  Let's try to printf a simple sentence.
  Length:[39, 39]
  Length:[39, 39]
  Negative:[-762534]
  Negative:[-762534]
  Unsigned:[2147484671]
  Unsigned:[2147484671]
  Unsigned octal:[20000001777]
  Unsigned octal:[20000001777]
  Unsigned hexadecimal:[800003ff, 800003FF]
  Unsigned hexadecimal:[800003ff, 800003FF]
  Character:[H]
  Character:[H]
  String:[I am a string !]
  String:[I am a string !]
  Address:[0x7ffe637541f0]
  Address:[0x7ffe637541f0]
  Percent:[%]
  Percent:[%]
  Len:[12]
  Len:[12]
  Unknown:[%r]
  Unknown:[%r]
  alex@ubuntu:~/c/printf$
  ```
- We strongly encourage you to work all together on a set of tests
- If the task does not specify what to do with an edge case, do the same as `printf`

## FILES

### HEADER FILE

| File     | Content                                                                                                                   |
| -------- | ------------------------------------------------------------------------------------------------------------------------- |
| _main.h_ | - This is an include guarded file that contains function prototypes of the different functions used to make this program. |

### MAN PAGE

| File           | Content                            |
| -------------- | ---------------------------------- |
| _man_3_printf_ | Usage: <br/> `man ./man_3_printf ` |

### FUNCTIONS

| File                 | Content                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| _\_printf.c_         | - Contains the `_printf` function.<br/>_Prototype_: `int _printf(const char *format , ...);`<br/>_Returns_ the number of characters written to string. Returns 1 on failure.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| _*get_print_func.c*_ | - a function that returns a pointer to a function based on the format specifier. <br/> - _Prototype_: `int (*get_print_func(char c))(va_list, int);`. <br/> - If format specifier doe not exist, it returns `NULL`. <br/> - Otherwise, it returns a function pointer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| _print_chars.c_      | - Contains two functions handling format specifier `%s and %c`. <br/>1. `print_ch()` - A function that writes characters to stdout. <br/>2. `print_str()` - Function that writes strings to stdout. <br/><br/>_Prototype_: <br/>1. `int print_ch(va_list args, int len);` <br/>2. `int print_str(va_list args, int len)`. <br/>_Return_: number of characters written.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| _print_numbers.c_    | - Contains four functions all handling format specifiers ` %d and %i`. <br> 1. `print *int()` - A function that checks for signed integers. <br> 2. `_putchar *int()` - A fuunction that writes signed integers to stdout. <br> 3. `print *numbers()` - A function that checks for numbers larger than `INT *MAX`. <br> 4. `find_length()` - A function that counts the digits in a numer.<br><br/> _Prototypes_: <br> 1. `int print_int(va_list args, int len)` <br> 2. `int _putchar_int(int n, int len)` <br>3. `int print_numbers(unsigned long n, unsigned int base, const char *digits)`<br> 4. `unsigned int find*length(unsigned int n, int base)`. <br>_Return_: <br> 1. An unsigned long integer and the current length of the number. <br> 2. Length of number written to stdout. <br> 3. A call to findlength. <br>4. Number of digits in a number. |
| _print_binary.c_     | - Contains two functions handling the custom format specifier `%b`.<br/> 1. `print_binary()` - A funtction that converts an int to binary.<br/> 2. `print_b()` - Initializes the arg to an unsigned int and calls `print_binary()`.<br/> <br/> _Prototype_: <br/> 1. `int print_b(va_list args, int len);`.<br/> 2. `int print_binary(unsigned int n, int len);`._Return_:<br/> 1. Length of printed binary.<br/> 2. The value returned by print\*binary                                                                                                                                                                                                                                                                                                                                                                                                        |
| _\_print_hex.c_      | - Contains two functions handling the format specifiers `%x and %X`.<br/> 1. `print_hex()` - A function that converts integer inputs to lowercase hexadecimal numbers.<br/> 2. `print_heX()` - A function that converts integer inputs to uppercase hexadecimal numbers.<br/><br/>_Prototype_:<br/>`int print_hex(va_list args, int len);`.<br/> 2. `int print_heX(va_list args, int len);`.<br/> _Return_: number of hexadecimal characters written.                                                                                                                                                                                                                                                                                                                                                                                                           |
| _\_print_octal.c_    | - Contains a function that handles the format specifier `%o`.<br/> 1. `print_octal()` - A function that coverts integer inputs to octal values.<br/><br/> _Prototype_: 1. `int print_octal(va_list args, int len);`.<br/>_Return_: Number of cotal character written to stdout.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| _print_rot13.c_      | - Contains a function that handles the format specifier `%R`.<br/> 1. `print_rot13()` - A function that prints a string encrypted using [ROT13](https://rot13.com/).<br/><br/>_Prototype_: `int print_rot13(va_list args, int len);`.<br/> _Return_: Number of characters written to stdout.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| _print_strings_      | - Contains a function that handles the format specifier `%S`.<br/> 1. `print_Str()` - prints the unprintable characters in their hexadecimal equivalent preceded with `\x0` for on digit characters and `\x` for charcters with more than one digit.<br/><br/>_Prototype_: `int print_Str(va_list args, int len);`.<br/> _Return_: Number of characters written to stdout.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
