1. `printf("%*s\n", "hello world")`
   
   In C, one can use `printf("%20s\n", string)` to print `string` with minimal 
   width.

   Instead of hardcoding that width value in the format string, one can use `*` 
   to specify it in an additional argument:

   ```c
   // main.c

   #include <stdio.h>

   int main(void) {
       printf("|%*s|\n", 20, "hello world");

       return 0;
   }
   ```

   ```shell
   $ gcc main.c && ./a.out
   |         hello world|
   ```

2. `printf("string1" "string2")`
   
   Multiple consecutive `string literal`s will be concatenated into a single one
   at compile time:

   ```c
   // main.c

   #include <assert.h>
   #include <string.h>
   #include <stdio.h>
   
   int main(void)
   {
           char *str = "hello"
                       "world"
                       "!";
           char *str2 = "hello\
   world!";
   
           assert(strncmp(str, str2, strlen(str)) == 0);
   
           printf("%s\n", str);
   
           return 0;
   }
   ```

   ```shell
   $ gcc main.c && ./a.out
   helloworld!
   ```
   
3. `idx_number[array]`

   ```c
   #include <stdio.h>

   int main(void) {
       int array[] = {1, 2, 3};

       printf("%d\n", 2[array]);
   }
   ```
   ```shell
   $ gcc main.c && ./a.out
   3
   ```

   `array[idx_number]` is the syntax sugar for `*(array + idx_number)`, according
   to the commutative law of addition, `array + idx_number` is equivalent to
   `idx_number + array`, thus `idx_number[array]` is equal to `array[idx_number]`
