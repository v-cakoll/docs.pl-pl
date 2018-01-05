---
title: "ICorProfilerCallback4::MovedReferences2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.MovedReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ce74455bd4c7aeae148a0882e3c1e846d34ba50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 — Metoda
Wywołuje się, by raportu nowy układ obiektów na stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych. Ta metoda jest wywoływana, jeśli zaimplementowano profilera [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu. To wywołanie zwrotne zastępuje [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metody, ponieważ może raportować większych zakresów obiektów, którego długość przekracza może zostać wyrażona w ULONG.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 [in] Liczba bloków ciągłe obiektów, które przeniesiona w wyniku kompaktowania wyrzucanie elementów bezużytecznych. Oznacza to, że wartość `cMovedObjectIDRanges` jest całkowity rozmiar `oldObjectIDRangeStart`, `newObjectIDRangeStart`, i `cObjectIDRangeLength` tablic.  
  
 Argumenty trzech kolejnych `MovedReferences2` tablice równoległych. Innymi słowy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, i `cObjectIDRangeLength[i]` dotyczą wszystkich jeden blok ciągłe obiektów.  
  
 `oldObjectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest stary (wstępne wyrzucanie elementów bezużytecznych) początkowy adres bloku ciągłym, live obiektów w pamięci.  
  
 `newObjectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest nowy adres początkowy (po wyrzucanie elementów bezużytecznych) bloku ciągłym, live obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 [in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku ciągłe obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, który odwołuje się do `oldObjectIDRangeStart` i `newObjectIDRangeStart` tablic.  
  
## <a name="remarks"></a>Uwagi  
 Kompaktowanie modułu zbierającego elementy bezużyteczne zwraca pamięci zajmowany przez obiekty martwy i kompaktuje, które zwolnienie miejsca. W związku z tym na żywo obiekty mogą być przeniesione w stercie, i `ObjectID` wartości rozdzielonych powiadomienia mogą ulec zmianie.  
  
 Przyjęto założenie, że istniejące `ObjectID` wartość (`oldObjectID`) znajduje się w następującym zakresie:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 W takim przypadku przesunięcie od początku zakresu do rozpoczęcia obiektu wygląda następująco:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Dla dowolnej wartości `i` znajdujący się w następującym zakresie:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 można obliczyć nowego `ObjectID` w następujący sposób:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Żadna z `ObjectID` wartości przekazywane przez `MovedReferences2` obowiązują podczas wywołania zwrotnego, ponieważ moduł garbage collector może znajdować się w środku przenoszenie obiektów z starego lokalizacji do nowej lokalizacji. W związku z tym profilery nie powinny podejmować próby sprawdź obiekty podczas `MovedReferences2` wywołania. A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego wskazuje, że wszystkie obiekty zostały przeniesione do nowej lokalizacji i inspekcji mogą być wykonywane.  
  
 Jeśli profilera implementuje zarówno [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsów, `MovedReferences2` metoda jest wywoływana przed [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metody, ale tylko wtedy, gdy `MovedReferences2` metoda skończy się pomyślnie. Profilery może zwrócić HRESULT, która wskazuje błędu na podstawie `MovedReferences2` metody, aby uniknąć wywołanie metody drugiego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [MovedReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)  
 [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
