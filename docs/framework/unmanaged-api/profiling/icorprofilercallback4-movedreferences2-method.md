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
ms.openlocfilehash: 79e54cde8757bbe690f9b7c4344a2a3cb19cf627
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499392"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 — Metoda
Wywołuje się, by zgłosić nowy układ obiektów w stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych. Ta metoda jest wywoływana, jeśli Profiler zaimplementuje Interfejs [ICorProfilerCallback4](icorprofilercallback4-interface.md) . To wywołanie zwrotne zastępuje metodę [ICorProfilerCallback:: MovedReferences —](icorprofilercallback-movedreferences-method.md) , ponieważ umożliwia raportowanie większych zakresów obiektów, których długość przekracza, co może być wyrażone w ulong.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 podczas Liczba bloków sąsiadujących obiektów, które zostały przeniesione w wyniku kompaktowania wyrzucania elementów bezużytecznych. Oznacza to, że wartość `cMovedObjectIDRanges` jest łącznym rozmiarem `oldObjectIDRangeStart` `newObjectIDRangeStart` tablic,, i `cObjectIDRangeLength` .  
  
 Następne trzy argumenty `MovedReferences2` są równoległymi tablicami. Innymi słowy,, `oldObjectIDRangeStart[i]` `newObjectIDRangeStart[i]` i `cObjectIDRangeLength[i]` wszystkie dotyczą pojedynczego bloku ciągłego obiektów.  
  
 `oldObjectIDRangeStart`  
 podczas Tablica `ObjectID` wartości, z których każdy jest starym (przed wyrzucaniem elementów bezużytecznych) adres początkowy bloku ciągłego, na żywo obiektów w pamięci.  
  
 `newObjectIDRangeStart`  
 podczas Tablica `ObjectID` wartości, z których każdy jest nowym (wyrzucanym po sobie) adresem początkowym bloku ciągłego, na żywo obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 podczas Tablica liczb całkowitych, z których każdy jest rozmiarem bloku ciągłych obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, do którego odwołuje się `oldObjectIDRangeStart` `newObjectIDRangeStart` Tablica i.  
  
## <a name="remarks"></a>Uwagi  
 Kompaktowy moduł zbierający elementy bezużyteczne odzyskuje pamięć zajmowaną przez martwe obiekty i kompaktuje to wolne miejsce. W związku z tym obiekty na żywo mogą być przenoszone w ramach sterty, a `ObjectID` wartości dystrybuowane przez poprzednie powiadomienia mogą ulec zmianie.  
  
 Załóżmy, że istniejąca `ObjectID` wartość ( `oldObjectID` ) znajduje się w następującym zakresie:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 W takim przypadku przesunięcie od początku zakresu do początku obiektu jest następujące:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Dla dowolnej wartości `i` , która znajduje się w następującym zakresie:  
  
 0 <=`i` < `cMovedObjectIDRanges`  
  
 nowe wartości można obliczyć `ObjectID` w następujący sposób:  
  
 `newObjectID` = `newObjectIDRangeStart[i]`+ ( `oldObjectID` – `oldObjectIDRangeStart[i]` )  
  
 Żadna z `ObjectID` wartości przesłanych przez nie `MovedReferences2` jest prawidłowa podczas wywołania zwrotnego, ponieważ moduł wyrzucania elementów bezużytecznych może być w trakcie przesuwania obiektów ze starych lokalizacji do nowych lokalizacji. W związku z tym nie należy próbować kontrolować obiektów podczas `MovedReferences2` wywołania. Wywołanie zwrotne [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) wskazuje, że wszystkie obiekty zostały przeniesione do nowej lokalizacji i można przeprowadzić inspekcję.  
  
 Jeśli profiler implementuje zarówno interfejsy [ICorProfilerCallback](icorprofilercallback-interface.md) , jak i [ICorProfilerCallback4](icorprofilercallback4-interface.md) , `MovedReferences2` Metoda jest wywoływana przed metodą [ICorProfilerCallback:: MovedReferences —](icorprofilercallback-movedreferences-method.md) , ale tylko wtedy, gdy `MovedReferences2` Metoda zwróci wartość pomyślnie. Program do tworzenia plików może zwrócić wynik HRESULT, który wskazuje niepowodzenie z `MovedReferences2` metody, aby uniknąć wywoływania drugiej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [MovedReferences, metoda](icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
