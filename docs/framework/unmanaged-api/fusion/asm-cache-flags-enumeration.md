---
title: ASM_CACHE_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
ms.openlocfilehash: 85ac976daec8fd76ee21012a30611235609f4b34
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109496"
---
# <a name="asm_cache_flags-enumeration"></a>ASM_CACHE_FLAGS — Wyliczenie
Wskazuje źródło zestawu, który jest reprezentowany przez [IAssemblyCacheItem](iassemblycacheitem-interface.md) w globalnej pamięci podręcznej zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|Wylicza pamięć podręczną wstępnie skompilowanych zestawów przy użyciu programu Ngen. exe.|  
|`ASM_CACHE_GAC`|Wylicza globalną pamięć podręczną zestawów.|  
|`ASM_CACHE_DOWNLOAD`|Wylicza zestawy, które zostały pobrane na żądanie lub które zostały skopiowane w tle.|  
|`ASM_CACHE_ROOT`|Wskazuje, że funkcja [GetCachePath —](getcachepath-function.md) powinna zwracać ścieżkę do globalnej pamięci podręcznej zestawów dla środowiska uruchomieniowego języka wspólnego (CLR) w wersji 2,0. Znaczenie tylko w kontekście wywołania do [GetCachePath —](getcachepath-function.md).|  
|`ASM_CACHE_ROOT_EX`|Wskazuje, że funkcja [GetCachePath —](getcachepath-function.md) powinna zwracać ścieżkę do globalnej pamięci podręcznej zestawów dla środowiska CLR w wersji 4. Znaczenie tylko w kontekście wywołania do [GetCachePath —](getcachepath-function.md).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetCachePath, funkcja](getcachepath-function.md)
- [IAssemblyCacheItem, interfejs](iassemblycacheitem-interface.md)
- [Wyliczenia łączenia](fusion-enumerations.md)
