---
title: ICorProfilerCallback2::SurvivingReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
ms.openlocfilehash: a83f8566dfe8e1b612f67d95a0e69947b72704ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439600"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences — Metoda
Raportuje układ obiektów w stercie w wyniku niekompaktowego wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 podczas Liczba bloków ciągłych obiektów, które przeżyły jako wynik niekompaktowego wyrzucania elementów bezużytecznych. Oznacza to, że wartość `cSurvivingObjectIDRanges` jest rozmiarem `objectIDRangeStart` i `cObjectIDRangeLength` tablic, które przechowują odpowiednio `ObjectID` i długość dla każdego bloku obiektów.  
  
 Dwa następne argumenty `SurvivingReferences` są tablicami równoległymi. Innymi słowy, `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłego obiektów.  
  
 `objectIDRangeStart`  
 podczas Tablica wartości `ObjectID`, z których każdy jest adresem początkowym bloku ciągłego, na żywo obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 podczas Tablica liczb całkowitych, z których każdy jest rozmiarem ciągłego bloku ciągłych obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, do którego odwołuje się tablica `objectIDRangeStart`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych. W przypadku obiektów, które są większe niż 4 GB, zamiast tego użyj metody [ICorProfilerCallback4:: SurvivingReferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) .  
  
 Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablice powinny być interpretowane w następujący sposób, aby określić, czy obiekt przeżyje odzyskiwanie pamięci. Załóżmy, że wartość `ObjectID` (`ObjectID`) znajduje się w następującym zakresie:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Dla każdej wartości `i`, która znajduje się w następującym zakresie, obiekt przeżyłył wyrzucanie elementów bezużytecznych:  
  
 0 < = `i` < `cSurvivingObjectIDRanges`  
  
 Niekompaktowe wyrzucanie elementów bezużytecznych przejmuje pamięć zajmowaną przez obiekty "martwe", ale nie kompaktuje ilości wolnego miejsca. W efekcie do sterty jest zwracana pamięć, ale nie są przenoszone żadne obiekty "na żywo".  
  
 Wywołania środowiska uruchomieniowego języka wspólnego (CLR) `SurvivingReferences` dla niekompaktowych kolekcji elementów bezużytecznych. W przypadku kompaktowania kolekcji elementów bezużytecznych zamiast niej wywoływana jest [ICorProfilerCallback:: MovedReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) . Pojedyncze wyrzucanie elementów bezużytecznych może być kompaktowania dla jednej generacji i niekompaktowania dla innych. W przypadku wyrzucania elementów bezużytecznych dla każdej konkretnej generacji Profiler otrzyma wywołanie zwrotne `SurvivingReferences` lub wywołanie zwrotne `MovedReferences`, ale nie oba.  
  
 Podczas konkretnego wyrzucania elementów bezużytecznych może zostać odebranych wiele `SurvivingReferences` wywołań zwrotnych z powodu ograniczonego wewnętrznego buforowania, wiele wątków zgłasza w przypadku wyrzucania elementów bezużytecznych serwera i z innych przyczyn. W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych informacje są kumulowane — wszystkie odwołania, które są zgłaszane w dowolnym `SurvivingReferences` wywołanie zwrotne przeżyły do wyrzucania elementów bezużytecznych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [SurvivingReferences2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
