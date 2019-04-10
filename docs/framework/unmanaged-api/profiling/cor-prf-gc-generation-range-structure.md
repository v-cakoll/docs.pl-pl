---
title: COR_PRF_GC_GENERATION_RANGE — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 646c4e37a7fab503a26557f9fdfc926b1186b17b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216707"
---
# <a name="corprfgcgenerationrange-structure"></a>COR_PRF_GC_GENERATION_RANGE — Struktura
W tym artykule opisano szeroką gamę (czyli bloku) pamięci, która jest w trakcie wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`generation`|Wartość [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) wyliczenie, które określa blok pamięci generacji, do której należy.|  
|`rangeStart`|Identyfikator obiektu, który określa lokalizację początkową bloku pamięci.|  
|`rangeLength`|Wskaźnik na liczbę całkowitą, która określa rozmiar użytej części bloku pamięci (oznacza to, ilości pamięci używanej w ramach bloku).|  
|`rangeLengthReserved`|Wskaźnik na liczbę całkowitą, która określa rozmiar bloku pamięci (oznacza to, że ilość pamięci zarezerwowanej dla bloku).|  
  
## <a name="remarks"></a>Uwagi  
 `rangeLength` Być dokładna wartość jest wyświetlana tylko wtedy, gdy [icorprofilerinfo2::getgenerationbounds —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) lub [icorprofilerinfo2::getobjectgeneration —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), obie wykorzystującymi `COR_PRF_GC_GENERATION_RANGE` struktury, jest wywoływana z [icorprofilercallback2::garbagecollectionstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) lub [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profiling — Struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
