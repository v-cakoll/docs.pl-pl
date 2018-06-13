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
ms.openlocfilehash: 9d6713a7f54f6a6d8dbf261ad45304e6ddbe24c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450720"
---
# <a name="corprfsnapshotinfo-enumeration"></a>COR_PRF_SNAPSHOT_INFO — Wyliczenie
Określa, ile kopii danych do przekazania migawki stosu w każdym wywołaniu profilera [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Elementy członkowskie|Opis|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Wskazuje, że wszystkie muszą być przekazywane wartości `StackSnapshotCallback` parametrów, z wyjątkiem `context` parametru.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Wskazuje, że wszystkie muszą być przekazywane wartości `StackSnapshotCallback` parametrów, takich jak `context` parametru.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Wskazuje, że będą używane jest prostsze, alternatywny przejście stosu algorytm.|  
  
## <a name="remarks"></a>Uwagi  
 Wartości, które są udostępniane przez `COR_PRF_SNAPSHOT_INFO` wyliczenia są przekazywane jako parametry [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [DoStackSnapshot, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
