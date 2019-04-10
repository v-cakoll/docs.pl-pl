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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7dfbba3cef8afadfc6e12e53ea328c4fc7165ca0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206762"
---
# <a name="corprfgcrootkind-enumeration"></a>COR_PRF_GC_ROOT_KIND — Wyliczenie
Wskazuje rodzaj głównego kolekcji wyrzucania elementów, który jest udostępniany przez [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`COR_PRF_GC_ROOT_STACK`|Katalog główny jest zmienną na stosie.|  
|`COR_PRF_GC_ROOT_FINALIZER`|Katalog główny jest wpis w kolejce finalizatora.|  
|`COR_PRF_GC_ROOT_HANDLE`|Katalog główny jest uchwytem kolekcji wyrzucania elementów.|  
|`COR_PRF_GC_ROOT_OTHER`|Rodzaj elementu głównego jest nieokreślona.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — Wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
