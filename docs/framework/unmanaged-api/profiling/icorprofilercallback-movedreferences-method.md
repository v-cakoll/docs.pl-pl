---
title: ICorProfilerCallback::MovedReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
ms.openlocfilehash: 1214182c95f7d0304ec920a2ea7dae91b1f4a790
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503342"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences — Metoda
Wywołuje się, by zgłosić nowy układ obiektów w stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 podczas Liczba bloków sąsiadujących obiektów, które zostały przeniesione w wyniku kompaktowania wyrzucania elementów bezużytecznych. Oznacza to, że wartość `cMovedObjectIDRanges` jest łącznym rozmiarem `oldObjectIDRangeStart` `newObjectIDRangeStart` tablic,, i `cObjectIDRangeLength` .  
  
 Następne trzy argumenty `MovedReferences` są równoległymi tablicami. Innymi słowy,, `oldObjectIDRangeStart[i]` `newObjectIDRangeStart[i]` i `cObjectIDRangeLength[i]` wszystkie dotyczą pojedynczego bloku ciągłego obiektów.  
  
 `oldObjectIDRangeStart`  
 podczas Tablica `ObjectID` wartości, z których każdy jest starym (przed wyrzucaniem elementów bezużytecznych) adres początkowy bloku ciągłego, na żywo obiektów w pamięci.  
  
 `newObjectIDRangeStart`  
 podczas Tablica `ObjectID` wartości, z których każdy jest nowym (wyrzucanym po sobie) adresem początkowym bloku ciągłego, na żywo obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 podczas Tablica liczb całkowitych, z których każdy jest rozmiarem bloku ciągłych obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, do którego odwołuje się `oldObjectIDRangeStart` `newObjectIDRangeStart` Tablica i.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Ta metoda zgłasza rozmiary `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych. Aby uzyskać rozmiar obiektów, które są większe niż 4 GB, należy zamiast tego użyć metody [ICorProfilerCallback4:: MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) .  
  
 Kompaktowy moduł zbierający elementy bezużyteczne odzyskuje pamięć zajmowaną przez martwe obiekty i kompaktuje to wolne miejsce. W związku z tym obiekty na żywo mogą być przenoszone w ramach sterty, a `ObjectID` wartości dystrybuowane przez poprzednie powiadomienia mogą ulec zmianie.  
  
 Załóżmy, że istniejąca `ObjectID` wartość ( `oldObjectID` ) znajduje się w następującym zakresie:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 W takim przypadku przesunięcie od początku zakresu do początku obiektu jest następujące:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Dla dowolnej wartości `i` , która znajduje się w następującym zakresie:  
  
 0 <=`i` < `cMovedObjectIDRanges`  
  
 nowe wartości można obliczyć `ObjectID` w następujący sposób:  
  
 `newObjectID` = `newObjectIDRangeStart[i]`+ ( `oldObjectID` – `oldObjectIDRangeStart[i]` )  
  
 Żadna z `ObjectID` wartości przesłanych przez nie `MovedReferences` jest prawidłowa podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może być w trakcie przeniesienia obiektów ze starych lokalizacji do nowych lokalizacji. W związku z tym nie należy próbować kontrolować obiektów podczas `MovedReferences` wywołania. Wywołanie zwrotne [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) wskazuje, że wszystkie obiekty zostały przeniesione do nowej lokalizacji i można przeprowadzić inspekcję.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [MovedReferences2, metoda](icorprofilercallback4-movedreferences2-method.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
