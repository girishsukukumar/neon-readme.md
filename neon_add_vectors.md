
## An example of Adding two vectors of length 8  and each element is 8 bits

In this example we intialize the first vector mat1 with 9 and second vector mat2 with 10
and then change the 3-rd element in mat1 to 5. Then we add the two vectors using neon vadd API
and print the result

````
#include <arm_neon.h>
#include <stdio.h>

main()
{

   int8x8_t matresult;
   int8x8_t mat1 ;
   int8x8_t mat2 ;
   int i ;
   int result ;
   mat1 = vdup_n_s8(9); /* Initalize all the elements of mat1 with  number 9 */
   mat2 = vdup_n_s8(10);  /* Initalize all the elements of mat2 with  number 10 */

   mat1 = vset_lane_s8(5, mat1, 3); /* Just change the 3 element of mat1to 5 */

   printf("Contents of mat1:   ");
   printf("%d ", vget_lane_s8(mat1,0));
   printf("%d ", vget_lane_s8(mat1,1));
   printf("%d ", vget_lane_s8(mat1,2));
   printf("%d ", vget_lane_s8(mat1,3));
   printf("%d ", vget_lane_s8(mat1,4));
   printf("%d ", vget_lane_s8(mat1,5));
   printf("%d ", vget_lane_s8(mat1,6));
   printf("%d ", vget_lane_s8(mat1,7));
   printf("\n");

   printf("Contents of mat2:   ");
   printf("%d ", vget_lane_s8(mat2,0));
   printf("%d ", vget_lane_s8(mat2,1));
   printf("%d ", vget_lane_s8(mat2,2));
   printf("%d ", vget_lane_s8(mat2,3));
   printf("%d ", vget_lane_s8(mat2,4));
   printf("%d ", vget_lane_s8(mat2,5));
   printf("%d ", vget_lane_s8(mat2,6));
   printf("%d ", vget_lane_s8(mat2,7));
   printf("\n");

   matresult = vadd_s8 (mat1,  mat2);
   printf("Result of Addition: ");
   printf("%d ", vget_lane_s8(matresult,0));
   printf("%d ", vget_lane_s8(matresult,1));
   printf("%d ", vget_lane_s8(matresult,2));
   printf("%d ", vget_lane_s8(matresult,2));
   printf("%d ", vget_lane_s8(matresult,3));
   printf("%d ", vget_lane_s8(matresult,4));
   printf("%d ", vget_lane_s8(matresult,5));
   printf("%d ", vget_lane_s8(matresult,6));
   printf("%d ", vget_lane_s8(matresult,7));
   printf("\n");
}
````
### How to compile the above program
````
gcc  -mcpu=cortex-a7 -ftree-vectorize   -mfloat-abi=hard -mfpu=neon neonadd.c
Output is the file a.out
````

### Result of the above program
````
pi@arjuna:~/neon $ ./a.out
Contents of mat1:   9 9 9 5 9 9 9 9
Contents of mat2:   10 10 10 10 10 10 10 10
Result of Addition: 19 19 19 15 19 19 19 19
pi@arjuna:~/neon $ !v
````
