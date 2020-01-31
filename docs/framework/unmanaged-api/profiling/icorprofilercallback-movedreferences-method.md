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
ms.openlocfilehash: 79fcaaba44956d90f9d074ade132dfc0bafd7d9e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866120"
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
 podczas Liczba bloków sąsiadujących obiektów, które zostały przeniesione w wyniku kompaktowania wyrzucania elementów bezużytecznych. Oznacza to, że wartość `cMovedObjectIDRanges` jest łącznym rozmiarem `oldObjectIDRangeStart`, `newObjectIDRangeStart`i `cObjectIDRangeLength` tablic.  
  
 Kolejne trzy argumenty `MovedReferences` są tablicami równoległymi. Innymi słowy, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`i `cObjectIDRangeLength[i]` wszystkie dotyczą pojedynczego bloku ciągłych obiektów.  
  
 `oldObjectIDRangeStart`  
 podczas Tablica wartości `ObjectID`, z których każdy jest starym (przed wyrzucaniem elementów bezużytecznych) adres początkowy bloku ciągłego, na żywo obiektów w pamięci.  
  
 `newObjectIDRangeStart`  
 podczas Tablica wartości `ObjectID`, z których każdy jest nowym (wyrzucaniem elementów bezużytecznych) adres początkowy bloku ciągłego, na żywo obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 podczas Tablica liczb całkowitych, z których każdy jest rozmiarem bloku ciągłych obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, do którego odwołuje się `oldObjectIDRangeStart` i `newObjectIDRangeStart`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych. Aby uzyskać rozmiar obiektów, które są większe niż 4 GB, należy zamiast tego użyć metody [ICorProfilerCallback4:: MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) .  
  
 Kompaktowy moduł zbierający elementy bezużyteczne odzyskuje pamięć zajmowaną przez martwe obiekty i kompaktuje to wolne miejsce. W związku z tym obiekty na żywo mogą być przenoszone w ramach sterty, a `ObjectID` wartości dystrybuowane przez poprzednie powiadomienia mogą ulec zmianie.  
  
 Załóżmy, że istniejąca wartość `ObjectID` (`oldObjectID`) znajduje się w następującym zakresie:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 W takim przypadku przesunięcie od początku zakresu do początku obiektu jest następujące:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Dla dowolnej wartości `i`, która znajduje się w następującym zakresie:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 nowe `ObjectID` można obliczyć w następujący sposób:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Żadna z wartości `ObjectID` przesłanych przez `MovedReferences` nie jest prawidłowa podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może być w trakcie przeniesienia obiektów ze starych lokalizacji do nowych lokalizacji. W związku z tym nie należy próbować kontrolować obiektów podczas wywołania `MovedReferences`. Wywołanie zwrotne [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) wskazuje, że wszystkie obiekty zostały przeniesione do nowej lokalizacji i można przeprowadzić inspekcję.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [MovedReferences2, metoda](icorprofilercallback4-movedreferences2-method.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
