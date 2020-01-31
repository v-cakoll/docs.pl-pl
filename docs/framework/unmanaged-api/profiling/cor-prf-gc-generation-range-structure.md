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
ms.openlocfilehash: 682aac9729519e0861ae6e6f60df78a30063c278
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867215"
---
# <a name="cor_prf_gc_generation_range-structure"></a>COR_PRF_GC_GENERATION_RANGE — Struktura
Opisuje zakres (czyli blok) pamięci, która jest niedo wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`generation`|Wartość wyliczenia [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , która określa generację, do której należy blok pamięci.|  
|`rangeStart`|Identyfikator obiektu, który określa lokalizację początkową bloku pamięci.|  
|`rangeLength`|Wskaźnik do liczby całkowitej, która określa rozmiar używanej części bloku pamięci (czyli ilość pamięci używanej w bloku).|  
|`rangeLengthReserved`|Wskaźnik do liczby całkowitej, która określa rozmiar bloku pamięci (czyli ilość pamięci zarezerwowanej dla bloku).|  
  
## <a name="remarks"></a>Uwagi  
 Wartość `rangeLength` ma być dokładna tylko wtedy, gdy [ICorProfilerInfo2:: GetGenerationBounds —](icorprofilerinfo2-getgenerationbounds-method.md) lub [ICorProfilerInfo2:: GetObjectGeneration —](icorprofilerinfo2-getobjectgeneration-method.md), z których obie używają struktury `COR_PRF_GC_GENERATION_RANGE`, jest wywoływana z metody [ICorProfilerCallback2:: GarbageCollectionStarted —](icorprofilercallback2-garbagecollectionstarted-method.md) lub [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profiling — struktury](profiling-structures.md)
