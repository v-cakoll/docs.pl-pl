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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da06ce49415317393b3489c2b8f97afc58f7c83b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191305"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences — Metoda
Raportuje układ obiektów w stercie wyrzucania elementów bezużytecznych bez kondensowania w wyniku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 [in] Liczba bloków ciągłych obiektów, które przetrwały wyrzucanie elementów bezużytecznych bez kondensowania w wyniku. Oznacza to, że wartość `cSurvivingObjectIDRanges` jest rozmiarem `objectIDRangeStart` i `cObjectIDRangeLength` tablic, które magazynu `ObjectID` i długość, odpowiednio dla każdego bloku obiektów.  
  
 Następne dwa argumenty `SurvivingReferences` są tablicami równoległych. Innymi słowy `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłych obiektów.  
  
 `objectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest początkowy adres bloku ciągłych, obiekty aktywne w pamięci.  
  
 `cObjectIDRangeLength`  
 [in] Tablica liczb całkowitych, z których każdy jest rozmiar sprawny bloku ciągłych obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, w której podano odwołanie w `objectIDRangeStart` tablicy.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych. W przypadku obiektów, które są większe niż 4 GB, użyj [icorprofilercallback4::survivingreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metody zamiast tego.  
  
 Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablic powinien być interpretowany w następujący sposób w celu określenia, czy obiekt przetrwały wyrzucanie elementów bezużytecznych. Przyjęto założenie, że `ObjectID` wartość (`ObjectID`) znajduje się w następującym zakresie:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Dla dowolnej wartości `i` znajdujący się w następującym zakresie, obiekt ma przetrwały wyrzucanie elementów bezużytecznych:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Wyrzucanie elementów bezużytecznych bez kondensowania odzyskuje pamięć zajęta przez obiekty "martwe", ale nie compact zwolnione miejsca. W rezultacie pamięci jest zwracany do sterty, ale żadne obiekty "na żywo" są przenoszone.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `SurvivingReferences` dla bez kondensowania wyrzucania elementów bezużytecznych. Do kompaktowania wyrzucania elementów bezużytecznych [icorprofilercallback::movedreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) zamiast tego wywoływany jest. Pojedynczy wyrzucania elementów bezużytecznych może być kompaktowania jeden generacji i bez kondensowania dla innego. Wyrzucanie elementów bezużytecznych na dowolnym konkretnej generacji, program profilujący wyświetlany żaden `SurvivingReferences` wywołanie zwrotne lub `MovedReferences` wywołania zwrotnego, ale nie oba.  
  
 Wiele `SurvivingReferences` wywołań zwrotnych mogą odebranych podczas określonego wyrzucania elementów bezużytecznych, ze względu na ograniczone wewnętrznego buforowania, wiele wątków raportowania w przypadku serwer wyrzucania elementów bezużytecznych i innych powodów. W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych, informacje są zbiorczej — wszystkie odwołania, które są zgłaszane w dowolnym `SurvivingReferences` wywołania zwrotnego przetrwać wyrzucania elementów bezużytecznych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [SurvivingReferences2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
