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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af8f1c9f5d5500dad675edf14ff2e89506530631
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621240"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 — Metoda
Raportuje układ obiektów w stercie wyrzucania elementów bezużytecznych bez kondensowania w wyniku. Ta metoda jest wywoływana, jeśli zaimplementowano program profilujący [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu. Zastępuje to wywołanie zwrotne [icorprofilercallback2::survivingreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ponieważ może raportować większych zakresów obiektów, których długości przekracza, jakie mogą być wyrażone w ULONG.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 [in] Liczba bloków ciągłych obiektów, które przetrwały wyrzucanie elementów bezużytecznych bez kondensowania w wyniku. Oznacza to, że wartość `cSurvivingObjectIDRanges` jest rozmiarem `objectIDRangeStart` i `cObjectIDRangeLength` tablic, które magazynu `ObjectID` i długość, odpowiednio dla każdego bloku obiektów.  
  
 Następne dwa argumenty `SurvivingReferences2` są tablicami równoległych. Innymi słowy `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłych obiektów.  
  
 `objectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest początkowy adres bloku ciągłych, obiekty aktywne w pamięci.  
  
 `cObjectIDRangeLength`  
 [in] Tablica liczb całkowitych, z których każdy jest rozmiar sprawny bloku ciągłych obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, w której podano odwołanie w `objectIDRangeStart` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablic powinien być interpretowany w następujący sposób w celu określenia, czy obiekt przetrwały wyrzucanie elementów bezużytecznych. Przyjęto założenie, że `ObjectID` wartość (`ObjectID`) znajduje się w następującym zakresie:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Dla dowolnej wartości `i` znajdujący się w następującym zakresie, obiekt ma przetrwały wyrzucanie elementów bezużytecznych:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Wyrzucanie elementów bezużytecznych bez kondensowania odzyskuje pamięć zajęta przez obiekty "martwe", ale nie compact zwolnione miejsca. W rezultacie pamięci jest zwracany do sterty, ale żadne obiekty "na żywo" są przenoszone.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `SurvivingReferences2` dla bez kondensowania wyrzucania elementów bezużytecznych. Do kompaktowania wyrzucania elementów bezużytecznych [movedreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) zamiast tego wywoływany jest. Pojedynczy wyrzucania elementów bezużytecznych może być kompaktowania jeden generacji i bez kondensowania dla innego. Wyrzucanie elementów bezużytecznych na dowolnym konkretnej generacji, program profilujący wyświetlany żaden `SurvivingReferences2` wywołanie zwrotne lub [movedreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) wywołania zwrotnego, ale nie oba.  
  
 Wiele `SurvivingReferences2` wywołania zwrotne może być odbierane podczas określonego wyrzucania elementów bezużytecznych, ze względu na ograniczone wewnętrznego buforowania, wiele wywołań zwrotnych podczas wyrzucania elementów bezużytecznych dla serwera i innych powodów. W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych informacje są zbiorcze; wszystkie odwołania, które są zgłaszane w dowolnym `SurvivingReferences2` wywołania zwrotnego przetrwać wyrzucania elementów bezużytecznych.  
  
 Gdy profiler implementuje zarówno [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsów, `SurvivingReferences2` metoda jest wywoływana przed [ICorProfilerCallback2:: Survivingreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ale tylko wtedy, gdy `SurvivingReferences2` wróci pomyślnie. Profilery może zwrócić HRESULT, która wskazuje błędu na podstawie `SurvivingReferences2` metodę, aby uniknąć wywoływania drugiej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
