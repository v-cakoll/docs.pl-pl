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
ms.openlocfilehash: 208ce1d7ef8a1eab4f18a6d488f0cc480b5713d8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499340"
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
 podczas Liczba bloków ciągłych obiektów, które przeżyły jako wynik niekompaktowego wyrzucania elementów bezużytecznych. Oznacza to, że wartość `cSurvivingObjectIDRanges` jest rozmiarem `objectIDRangeStart` `cObjectIDRangeLength` tablic i, które przechowują `ObjectID` odpowiednio długość i dla każdego bloku obiektów.  
  
 Dwa następne argumenty `SurvivingReferences2` są równoległymi tablicami. Innymi słowy `objectIDRangeStart` i dotyczy tego `cObjectIDRangeLength` samego bloku sąsiadujących obiektów.  
  
 `objectIDRangeStart`  
 podczas Tablica `ObjectID` wartości, z których każdy jest adresem początkowym bloku ciągłego, na żywo obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 podczas Tablica liczb całkowitych, z których każdy jest rozmiarem ciągłego bloku ciągłych obiektów w pamięci.  
  
 Dla każdego bloku, do którego odwołuje się tablica, jest określony rozmiar `objectIDRangeStart` .  
  
## <a name="remarks"></a>Uwagi  
 Elementy `objectIDRangeStart` `cObjectIDRangeLength` tablic i powinny być interpretowane w następujący sposób, aby określić, czy obiekt przeżyje odzyskiwanie pamięci. Załóżmy, że `ObjectID` wartość ( `ObjectID` ) znajduje się w następującym zakresie:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Dla każdej wartości `i` , która znajduje się w następującym zakresie, obiekt przeżyły odzyskiwanie pamięci:  
  
 0 <=`i` < `cSurvivingObjectIDRanges`  
  
 Niekompaktowe wyrzucanie elementów bezużytecznych przejmuje pamięć zajmowaną przez obiekty "martwe", ale nie kompaktuje ilości wolnego miejsca. W efekcie do sterty jest zwracana pamięć, ale nie są przenoszone żadne obiekty "na żywo".  
  
 Wywołania środowiska uruchomieniowego języka wspólnego (CLR) `SurvivingReferences2` dla niekompaktowych kolekcji elementów bezużytecznych. W przypadku kompaktowania kolekcji elementów bezużytecznych jest wywoływana [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) . Pojedyncze wyrzucanie elementów bezużytecznych może być kompaktowania dla jednej generacji i niekompaktowania dla innych. W przypadku wyrzucania elementów bezużytecznych na określonej generacji Profiler otrzyma `SurvivingReferences2` wywołanie zwrotne lub wywołanie zwrotne [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) , ale nie oba.  
  
 `SurvivingReferences2`Podczas konkretnego wyrzucania elementów bezużytecznych może zostać odebranych wiele wywołań zwrotnych z powodu ograniczonego wewnętrznego buforowania, wielu wywołań zwrotnych podczas odzyskiwania pamięci serwera i innych przyczyn. W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych informacja jest zbiorcza; wszystkie odwołania, które są zgłaszane w przypadku `SurvivingReferences2` wywołania zwrotnego w trakcie wyrzucania elementów bezużytecznych.  
  
 Jeśli profiler implementuje zarówno interfejsy [ICorProfilerCallback](icorprofilercallback-interface.md) , jak i [ICorProfilerCallback4](icorprofilercallback4-interface.md) , `SurvivingReferences2` Metoda jest wywoływana przed metodą [ICorProfilerCallback2:: SurvivingReferences —](icorprofilercallback2-survivingreferences-method.md) , ale tylko wtedy, gdy `SurvivingReferences2` zwróci wartość pomyślnie. Obiekt profilowający może zwracać wynik HRESULT, który wskazuje niepowodzenie z `SurvivingReferences2` metody, aby uniknąć wywoływania drugiej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 — Interfejs](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
