**
Notes 

URLS
https://stackoverflow.com/questions/28547697/coding-for-arm-neon-how-to-start

Compiling Neon source code
gcc  -mcpu=cortex-a7 -ftree-vectorize   -mfloat-abi=hard -mfpu=neon test.c
/* 28-Dec-2017 */
#include <arm_neon.h>

main()
{
}

