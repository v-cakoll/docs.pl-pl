---
title: "ASM_CACHE_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 87dce9a2daf7067409d78a9f389695b6b01f23c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="asmcacheflags-enumeration"></a>ASM_CACHE_FLAGS — Wyliczenie
Wskazuje źródło zestawu, który jest reprezentowana przez [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) w globalnej pamięci podręcznej zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|Wylicza pamięci podręcznej w zestawach wstępnie skompilowanych przy użyciu Ngen.exe.|  
|`ASM_CACHE_GAC`|Wylicza globalnej pamięci podręcznej zestawów.|  
|`ASM_CACHE_DOWNLOAD`|Wylicza zestawy, które zostały pobrane na żądanie lub które zostały skopiowane w tle.|  
|`ASM_CACHE_ROOT`|Oznacza to, że [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) funkcja powinna zwrócić ścieżka do pamięci podręcznej GAC środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0. Znaczenie tylko w kontekście wywołania [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).|  
|`ASM_CACHE_ROOT_EX`|Oznacza to, że [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) funkcja powinna zwrócić ścieżki globalnej pamięci podręcznej zestawów dla CLR w wersji 4. Znaczenie tylko w kontekście wywołania [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetCachePath, funkcja](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [IAssemblyCacheItem, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [Wyliczenia łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
