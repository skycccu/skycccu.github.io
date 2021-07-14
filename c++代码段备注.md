加密级别的随机数算法

```
#include "windows.h"
#include "wincrypt.h"
#include "iostream"
#include "cassert"
#include "stdlib.h"

int GetRandom() {
    int rnum = 0;

    //CeGenRandom(sizeof(int), (PBYTE)&rnum);

    HCRYPTPROV hProvider = 0;
    const DWORD dwLength = sizeof(int);
    BYTE pbBuffer[dwLength] = {};
    DWORD result =::CryptAcquireContext(&hProvider, 0, 0, PROV_RSA_FULL, CRYPT_VERIFYCONTEXT | CRYPT_SILENT);
    assert(result);
    result = ::CryptGenRandom(hProvider, dwLength, pbBuffer);
    rnum = *(int*)pbBuffer;
    assert(result);
    ::CryptReleaseContext(hProvider, 0);
    
    return abs(rnum);
}

int main()
{
    int v1=0;
    int v2=0;
    int v3=0;
    int v4=0;
    int v5=0;
    int v6=0;
    int pre=0;
    int r=0;
    int res=0;

    for(int i=0;i<100000;i++){
        res = GetRandom();
        r = res % 54;
        printf("Unsigned: : %d\n",r);
        
        if(pre!=0 && r == pre) v6++;
        pre = r;
        
        if(r <= 1){
             v1++;
        }else if(r <= 14){
              v2++;
        }else if(r <= 27){
              v3++;
        }else if(r <= 40){
              v4++;
        }else{
              v5++;
        }  
    }
    printf("v1:%d, v2:%d, v3:%d, v4:%d, v5:%d, v6:%d,\n",v1,v2,v3,v4,v5,v6);
    system("pause");
    return 0;
}
```