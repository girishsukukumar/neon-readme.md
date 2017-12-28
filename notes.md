# Study of Neon Processor
## URLS
1. https://stackoverflow.com/questions/28547697/coding-for-arm-neon-how-to-start
1. http://infocenter.arm.com/help/topic/com.arm.doc.ihi0073a/IHI0073A_arm_neon_intrinsics_ref.pdf
1. http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0472j/chr1360928373893.html

## Compiling Neon source code
```
gcc  -mcpu=cortex-a7 -ftree-vectorize   -mfloat-abi=hard -mfpu=neon test.c

/* 28-Dec-2017 */
#include <arm_neon.h>

main()
{
}
```
