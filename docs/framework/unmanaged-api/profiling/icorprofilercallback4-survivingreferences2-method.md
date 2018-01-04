---
title: "ICorProfilerCallback4::SurvivingReferences2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.SurvivingReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db40e908421c45e9d4192c436995d8137f81ec0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 — Metoda
Raporty układ obiektów na stercie wyniku-kompaktowania wyrzucania elementów bezużytecznych. Ta metoda jest wywoływana, jeśli zaimplementowano profilera [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu. To wywołanie zwrotne zastępuje [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ponieważ może raportować większych zakresów obiektów, którego długość przekracza może zostać wyrażona w ULONG.  
  
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
 [in] Liczba bloków ciągłe obiektów, które udało przetrwać wyniku-kompaktowania wyrzucanie elementów bezużytecznych. Oznacza to, że wartość `cSurvivingObjectIDRanges` rozmiar `objectIDRangeStart` i `cObjectIDRangeLength` stałych, w których magazyn `ObjectID` oraz długość, odpowiednio do każdego bloku obiektów.  
  
 Następne dwa argumenty `SurvivingReferences2` tablice równoległych. Innymi słowy `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłe obiektów.  
  
 `objectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest adres początkowy blok ciągłym, live obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 [in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku sprawny ciągłe obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, który odwołuje się do `objectIDRangeStart` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablice powinny być rozumiane w następujący sposób, aby określić, czy udało się obiektu przetrwać wyrzucanie elementów bezużytecznych. Przyjęto założenie, że `ObjectID` wartość (`ObjectID`) znajduje się w następującym zakresie:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Dla dowolnej wartości `i` znajdujący się w następującym zakresie, obiekt ma udało przetrwać wyrzucanie elementów bezużytecznych:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Kompaktowania wyrzucania elementów bezużytecznych zwraca pamięci zajmowany przez obiekty "martwy", ale nie compact zwolnionych miejsca. W związku z tym pamięci jest zwracany do sterty, ale żadne obiekty "na żywo" są przenoszone.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `SurvivingReferences2` dla-kompaktowania wyrzucanie elementów bezużytecznych. Kolekcje garbage kompaktowania [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) jest wywoływana zamiast tego. Pojedynczy wyrzucania elementów bezużytecznych można kompaktowania jeden generacji i z systemem innym niż kompaktowania dla innej. Wyrzucanie elementów bezużytecznych na dowolnym określonym generacji profilera wyświetlany żaden `SurvivingReferences2` wywołania zwrotnego lub [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) wywołania zwrotnego, ale nie oba.  
  
 Wiele `SurvivingReferences2` wywołania zwrotne może odbierane podczas określonego wyrzucania elementów bezużytecznych, ze względu na ograniczone buforowanie wewnętrznego, wielu wywołań zwrotnych podczas odzyskiwanie pamięci na serwerze i innych powodów. W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych informacje są zbiorczą; wszystkie odwołania zgłaszanych w żadnym `SurvivingReferences2` wywołania zwrotnego przetrwać wyrzucanie elementów bezużytecznych.  
  
 Jeśli profilera implementuje zarówno [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsów, `SurvivingReferences2` metoda jest wywoływana przed [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ale tylko wtedy, gdy `SurvivingReferences2` zwraca pomyślnie. Profilery może zwrócić HRESULT, która wskazuje błędu na podstawie `SurvivingReferences2` metody w celu uniknięcia wywołanie metody drugiego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
