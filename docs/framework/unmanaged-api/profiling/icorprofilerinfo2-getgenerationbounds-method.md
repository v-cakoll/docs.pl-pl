---
title: "ICorProfilerInfo2::GetGenerationBounds — Metoda"
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
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c84be5d7e78c348c0368e9639a470a8fc60e2ca7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds — Metoda
Pobiera regiony pamięci, które są segmentów sterty, wchodzące w skład różnych generacji wyrzucania elementów w kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cObjectRanges`  
 [in] Liczba elementów przydzielone przez obiekt wywołujący dla `ranges` tablicy.  
  
 `pcObjectRanges`  
 [out] Wskaźnik do wartości całkowitej, łączna liczba zakresów, który określa niektóre lub wszystkie z nich zostaną zwrócone w `ranges` tablicy.  
  
 `ranges`  
 [out] Tablica [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury, z których każdy zawiera opis zakresu (to znaczy bloku) pamięci w ramach wybranej generacji jest poddawana wyrzucanie elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
 `GetGenerationBounds` Można wywołać metody zwrotne profilera, pod warunkiem, że pamięci nie jest w toku. Oznacza to, może zostać wywołana z dowolnego wywołania zwrotnego z wyjątkiem tych, które mają miejsce między [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) i [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
 Większość zmieni pokoleń odbywa się podczas odzyskiwania. Generacje mogą rosnąć między kolekcji, ale zwykle nie należy przenosić. W związku z tym najbardziej interesujące miejsca do wywołania `GetGenerationBounds` w `ICorProfilerCallback2::GarbageCollectionStarted` i `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Podczas uruchamiania programu niektóre obiekty są przydzielane przez środowisko uruchomieniowe języka wspólnego (CLR), zazwyczaj w generacje 3 i 0. W związku z tym w czasie kodu zarządzanego rozpoczyna wykonywanie tych generacje już będzie zawierać obiektów. Zwykle jest pusta, z wyjątkiem fikcyjny obiektów, które są generowane przez moduł garbage collector generacji 1 i 2. (Rozmiar fikcyjny obiektów jest 12 bajtów w implementacjach 32-bitowego środowiska CLR; rozmiar jest większy w implementacjach 64-bitowe). Może być również wyświetlany zakresy generacji 2, które znajdują się wewnątrz modułów utworzonego przez Generator obrazu natywnego (NGen.exe). W takim przypadku obiekt w generacji 2 są *zablokowane obiekty*, które są przydzielane po uruchomieniu NGen.exe, a nie przez moduł garbage collector.  
  
 Ta funkcja korzysta buforów przydzielone przez obiekt wywołujący.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
