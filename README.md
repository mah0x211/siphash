# siphash.h

siphash header library.  

referenced from;
- https://131002.net/siphash/  
- https://131002.net/siphash/siphash.pdf

---

siphash -- returns a 64 bit hash value.

```c
#include "siphash.h"

uint64_t siphash( const uint8_t rblk, const uint8_t rfin, const uint64_t key[2], const void *src, size_t len );
```

**Parameters**

- `rblk`: the number of rounds per message block.
- `rfin`: the number of finalization rounds.
- `key`: 128 bit secret key.
- `src`: message.
- `len`: message length.

**Return Values**

siphash() function returns a 64 bit hash value.

**Helper Macros**

- `siphash24( key, src, len )`
- `siphash48( key, src, len )`


## Usage

```c
#include <stdio.h>
#include <string.h>
#include "siphash.h"

int main (int argc, const char * argv[])
{
    uint64_t key[2] = {
        0xdeadbeefcafebabe, 
        0x8badf00d1badb002
    };
    char *msg = "Hello, World!";
    uint64_t res = siphash( 2, 4, key, msg, strlen( msg ) );
    
    // Hello, World! -> 10097994589113331027
    printf( "%s -> %llu\n", msg, res );
    
    return 0;
}
```
