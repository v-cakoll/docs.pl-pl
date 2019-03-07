---
title: ICorProfilerCallback4::MovedReferences2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9878252fb61dabe3154df90265229f160bb80d10
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484423"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 — Metoda
Wywołuje się, aby zgłosić nowy układ obiektów w stercie wyniku kompaktowania wyrzucania elementów bezużytecznych. Ta metoda jest wywoływana, jeśli zaimplementowano program profilujący [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu. Zastępuje to wywołanie zwrotne [icorprofilercallback::movedreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metody, ponieważ może raportować większych zakresów obiektów, których długości przekracza, jakie mogą być wyrażone w ULONG.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 [in] Liczba bloków ciągłych obiektów, które przeniesione w wyniku kompaktowania wyrzucania elementów bezużytecznych. Oznacza to, że wartość `cMovedObjectIDRanges` jest całkowity rozmiar `oldObjectIDRangeStart`, `newObjectIDRangeStart`, i `cObjectIDRangeLength` tablic.  
  
 Następne trzy argumenty `MovedReferences2` są tablicami równoległych. Innymi słowy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, i `cObjectIDRangeLength[i]` dotyczą wszystkich jeden blok ciągłych obiektów.  
  
 `oldObjectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest stary (wstępne wyrzucania elementów bezużytecznych) początkowy adres bloku ciągłych, obiekty aktywne w pamięci.  
  
 `newObjectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest nowy adres początkowy (po wyrzucania elementów bezużytecznych), bloku ciągłych, obiekty aktywne w pamięci.  
  
 `cObjectIDRangeLength`  
 [in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku ciągłych obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, w której podano odwołanie w `oldObjectIDRangeStart` i `newObjectIDRangeStart` tablic.  
  
## <a name="remarks"></a>Uwagi  
 Kompaktowania moduł odśmiecania pamięci odzyskuje pamięć zajęta przez obiekty martwe i kompaktuje, które zwolnienie miejsca. W rezultacie obiekty na żywo mogą być przeniesione w stosie, i `ObjectID` wartości rozdzielonych powiadomienia mogą ulec zmianie.  
  
 Przyjęto założenie, że istniejące `ObjectID` wartość (`oldObjectID`) znajduje się w następującym zakresie:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 W tym przypadku przesunięcie od początku zakresu do rozpoczęcia obiektu jest następująca:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Dla dowolnej wartości `i` znajdujący się w następującym zakresie:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 można obliczyć nową `ObjectID` w następujący sposób:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Żaden z `ObjectID` wartości przekazanych przez `MovedReferences2` obowiązują podczas wywołania zwrotnego, ponieważ moduł odśmiecania pamięci może być w trakcie przenoszenia obiektów z lokalizacji starej do nowej lokalizacji. W związku z tym, profilowania nie należy próbować Zbadaj obiekty podczas `MovedReferences2` wywołania. A [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego wskazuje, że wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i inspekcji mogą być wykonywane.  
  
 Gdy profiler implementuje zarówno [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsów, `MovedReferences2` metoda jest wywoływana przed [ICorProfilerCallback:: Movedreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metody, ale tylko wtedy, gdy `MovedReferences2` metoda zwraca pomyślnie. Profilery może zwrócić HRESULT, która wskazuje błędu na podstawie `MovedReferences2` metody, aby uniknąć wywoływania drugiej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [MovedReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
