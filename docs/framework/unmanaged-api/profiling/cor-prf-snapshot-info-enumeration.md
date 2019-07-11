---
title: COR_PRF_SNAPSHOT_INFO — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9a7d55b5a4867dcdc4e816bd3eac2cf29c68564
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751979"
---
# <a name="corprfsnapshotinfo-enumeration"></a>COR_PRF_SNAPSHOT_INFO — Wyliczenie
Określa, ile danych do przekazania z powrotem za pomocą migawki stosu w każdym wywołaniu do programu profilującego [stacksnapshotcallback —](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Elementy członkowskie|Opis|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Wskazuje, że wszystkie muszą być przekazywane wartości `StackSnapshotCallback` parametry, z wyjątkiem `context` parametru.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Wskazuje, że wszystkie muszą być przekazywane wartości `StackSnapshotCallback` parametrów, w tym `context` parametru.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Wskazuje, czy prostszy, alternatywnych zalet stosu algorytm będzie używany.|  
  
## <a name="remarks"></a>Uwagi  
 Wartości, które są dostarczane przez `COR_PRF_SNAPSHOT_INFO` wyliczenia są przekazywane jako parametry do [dostacksnapshot —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [DoStackSnapshot, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
