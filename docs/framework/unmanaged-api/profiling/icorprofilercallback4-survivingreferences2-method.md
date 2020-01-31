---
title: ICorProfilerCallback4::SurvivingReferences2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
ms.openlocfilehash: bec50183e6a8690cb02f3dc06d32b7449e055cea
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865171"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 — Metoda
Raportuje układ obiektów w stercie w wyniku niekompaktowego wyrzucania elementów bezużytecznych. Ta metoda jest wywoływana, jeśli Profiler zaimplementuje Interfejs [ICorProfilerCallback4](icorprofilercallback4-interface.md) . To wywołanie zwrotne zastępuje metodę [ICorProfilerCallback2:: SurvivingReferences —](icorprofilercallback2-survivingreferences-method.md) , ponieważ umożliwia raportowanie większych zakresów obiektów, których długość przekracza, co może być wyrażone w ulong.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 podczas Liczba bloków ciągłych obiektów, które przeżyły jako wynik niekompaktowego wyrzucania elementów bezużytecznych. Oznacza to, że wartość `cSurvivingObjectIDRanges` jest rozmiarem `objectIDRangeStart` i `cObjectIDRangeLength` tablic, które przechowują odpowiednio `ObjectID` i długość dla każdego bloku obiektów.  
  
 Dwa następne argumenty `SurvivingReferences2` są tablicami równoległymi. Innymi słowy, `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłego obiektów.  
  
 `objectIDRangeStart`  
 podczas Tablica wartości `ObjectID`, z których każdy jest adresem początkowym bloku ciągłego, na żywo obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 podczas Tablica liczb całkowitych, z których każdy jest rozmiarem ciągłego bloku ciągłych obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, do którego odwołuje się tablica `objectIDRangeStart`.  
  
## <a name="remarks"></a>Uwagi  
 Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablice powinny być interpretowane w następujący sposób, aby określić, czy obiekt przeżyje odzyskiwanie pamięci. Załóżmy, że wartość `ObjectID` (`ObjectID`) znajduje się w następującym zakresie:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Dla każdej wartości `i`, która znajduje się w następującym zakresie, obiekt przeżyłył wyrzucanie elementów bezużytecznych:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Niekompaktowe wyrzucanie elementów bezużytecznych przejmuje pamięć zajmowaną przez obiekty "martwe", ale nie kompaktuje ilości wolnego miejsca. W efekcie do sterty jest zwracana pamięć, ale nie są przenoszone żadne obiekty "na żywo".  
  
 Wywołania środowiska uruchomieniowego języka wspólnego (CLR) `SurvivingReferences2` dla niekompaktowych kolekcji elementów bezużytecznych. W przypadku kompaktowania kolekcji elementów bezużytecznych jest wywoływana [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) . Pojedyncze wyrzucanie elementów bezużytecznych może być kompaktowania dla jednej generacji i niekompaktowania dla innych. W przypadku wyrzucania elementów bezużytecznych dla każdej konkretnej generacji Profiler otrzyma wywołanie zwrotne `SurvivingReferences2` lub wywołanie zwrotne [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) , ale nie oba.  
  
 Podczas konkretnego wyrzucania elementów bezużytecznych może zostać odebranych wiele `SurvivingReferences2` wywołań zwrotnych z powodu ograniczonego wewnętrznego buforowania, wielu wywołań zwrotnych podczas odzyskiwania pamięci serwera i innych przyczyn. W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych informacja jest zbiorcza; wszystkie odwołania, które są zgłaszane w dowolnym `SurvivingReferences2` wywołanie zwrotne przeżyły do wyrzucania elementów bezużytecznych.  
  
 Jeśli profiler implementuje zarówno interfejsy [ICorProfilerCallback](icorprofilercallback-interface.md) , jak i [ICorProfilerCallback4](icorprofilercallback4-interface.md) , Metoda `SurvivingReferences2` jest wywoływana przed metodą [ICorProfilerCallback2:: SurvivingReferences —](icorprofilercallback2-survivingreferences-method.md) , ale tylko wtedy, gdy `SurvivingReferences2` zwróci się pomyślnie. Preplikcy mogą zwracać wynik HRESULT, który wskazuje niepowodzenie z metody `SurvivingReferences2`, aby uniknąć wywoływania drugiej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
