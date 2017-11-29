---
title: "ICorProfilerCallback2::SurvivingReferences — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.SurvivingReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3764bfb79b39af897600202e8bc0f2ffbc4da95b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences — Metoda
Raporty układ obiektów na stercie wyniku-kompaktowania wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 [in] Liczba bloków ciągłe obiektów, które udało przetrwać wyniku-kompaktowania wyrzucanie elementów bezużytecznych. Oznacza to, że wartość `cSurvivingObjectIDRanges` rozmiar `objectIDRangeStart` i `cObjectIDRangeLength` stałych, w których magazyn `ObjectID` oraz długość, odpowiednio do każdego bloku obiektów.  
  
 Następne dwa argumenty `SurvivingReferences` tablice równoległych. Innymi słowy `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłe obiektów.  
  
 `objectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest adres początkowy blok ciągłym, live obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 [in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku sprawny ciągłe obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, który odwołuje się do `objectIDRangeStart` tablicy.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych. Dla obiektów, które są większe niż 4 GB, użyj [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metody zamiast tego.  
  
 Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablice powinny być rozumiane w następujący sposób, aby określić, czy udało się obiektu przetrwać wyrzucanie elementów bezużytecznych. Przyjęto założenie, że `ObjectID` wartość (`ObjectID`) znajduje się w następującym zakresie:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Dla dowolnej wartości `i` znajdujący się w następującym zakresie, obiekt ma udało przetrwać wyrzucanie elementów bezużytecznych:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Kompaktowania wyrzucania elementów bezużytecznych zwraca pamięci zajmowany przez obiekty "martwy", ale nie compact zwolnionych miejsca. W związku z tym pamięci jest zwracany do sterty, ale żadne obiekty "na żywo" są przenoszone.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `SurvivingReferences` dla-kompaktowania wyrzucanie elementów bezużytecznych. Kolekcje garbage kompaktowania [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) jest wywoływana zamiast tego. Pojedynczy wyrzucania elementów bezużytecznych można kompaktowania jeden generacji i z systemem innym niż kompaktowania dla innej. Wyrzucanie elementów bezużytecznych na dowolnym określonym generacji profilera wyświetlany żaden `SurvivingReferences` wywołania zwrotnego lub `MovedReferences` wywołania zwrotnego, ale nie oba.  
  
 Wiele `SurvivingReferences` wywołania zwrotne może otrzymał podczas określonego wyrzucania elementów bezużytecznych, ze względu na ograniczone buforowania wewnętrznego, wiele wątków raportowania w przypadku odzyskiwanie pamięci na serwerze i innych powodów. W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych, informacje są zbiorcza — wszystkich odwołań, które są zgłaszane w żadnym `SurvivingReferences` wywołania zwrotnego przetrwać wyrzucanie elementów bezużytecznych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [SurvivingReferences2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
