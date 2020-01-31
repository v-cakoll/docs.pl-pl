---
title: COR_PRF_GC_ROOT_KIND — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: bff45e6f6f57b95d07ac5073cb70020818cce000
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867168"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a>COR_PRF_GC_ROOT_KIND — Wyliczenie
Wskazuje rodzaj katalogu głównego wyrzucania elementów bezużytecznych, który jest udostępniany przez wywołanie zwrotne [ICorProfilerCallback2:: RootReferences2 —](icorprofilercallback2-rootreferences2-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|Element główny jest zmienną na stosie.|  
|`COR_PRF_GC_ROOT_FINALIZER`|Katalog główny jest wpisem w kolejce finalizatora.|  
|`COR_PRF_GC_ROOT_HANDLE`|Katalog główny jest dojściem do wyrzucania elementów bezużytecznych.|  
|`COR_PRF_GC_ROOT_OTHER`|Rodzaj elementu głównego jest nieokreślony.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
