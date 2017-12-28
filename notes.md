# Study of Neon Processor
## URLS
1. https://stackoverflow.com/questions/28547697/coding-for-arm-neon-how-to-start
1. http://infocenter.arm.com/help/topic/com.arm.doc.ihi0073a/IHI0073A_arm_neon_intrinsics_ref.pdf
1. http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0472j/chr1360928373893.html
1. https://people.xiph.org/~tterribe/daala/neon_tutorial.pdf
1. https://developer.arm.com/technologies/neon/intrinsics  - Complete reference about Neon API

## Compiling Neon source code
```
gcc  -mcpu=cortex-a7 -ftree-vectorize   -mfloat-abi=hard -mfpu=neon test.c

/* 28-Dec-2017 */
#include <arm_neon.h>

main()
{
}
```
## An example of Adding two vectors of length 8 elements and each element is 8 bits

In this example we intialize two vectors will same data and then change the data in one of the elements.
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
