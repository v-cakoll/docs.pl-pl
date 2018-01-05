---
title: "ICorProfilerCallback::MovedReferences — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.MovedReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type: apiref
caps.latest.revision: "26"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d62fbdf4b6dd2acbb67b0655938990d625f8df8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences — Metoda
Wywołuje się, by raportu nowy układ obiektów na stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 [in] Liczba bloków ciągłe obiektów, które przeniesiona w wyniku kompaktowania wyrzucanie elementów bezużytecznych. Oznacza to, że wartość `cMovedObjectIDRanges` jest całkowity rozmiar `oldObjectIDRangeStart`, `newObjectIDRangeStart`, i `cObjectIDRangeLength` tablic.  
  
 Argumenty trzech kolejnych `MovedReferences` tablice równoległych. Innymi słowy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, i `cObjectIDRangeLength[i]` dotyczą wszystkich jeden blok ciągłe obiektów.  
  
 `oldObjectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest stary (wstępne wyrzucanie elementów bezużytecznych) początkowy adres bloku ciągłym, live obiektów w pamięci.  
  
 `newObjectIDRangeStart`  
 [in] Tablica `ObjectID` wartości, z których każdy jest nowy adres początkowy (po wyrzucanie elementów bezużytecznych) bloku ciągłym, live obiektów w pamięci.  
  
 `cObjectIDRangeLength`  
 [in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku ciągłe obiektów w pamięci.  
  
 Rozmiar jest określony dla każdego bloku, który odwołuje się do `oldObjectIDRangeStart` i `newObjectIDRangeStart` tablic.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych. Aby uzyskać rozmiar obiektów, które są większe niż 4 GB, należy użyć [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metody zamiast tego.  
  
 Kompaktowanie modułu zbierającego elementy bezużyteczne zwraca pamięci zajmowany przez obiekty martwy i kompaktuje, które zwolnienie miejsca. W związku z tym na żywo obiekty mogą być przeniesione w stercie, i `ObjectID` wartości rozdzielonych powiadomienia mogą ulec zmianie.  
  
 Przyjęto założenie, że istniejące `ObjectID` wartość (`oldObjectID`) znajduje się w następującym zakresie:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 W takim przypadku przesunięcie od początku zakresu do rozpoczęcia obiektu wygląda następująco:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Dla dowolnej wartości `i` znajdujący się w następującym zakresie:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 można obliczyć nowego `ObjectID` w następujący sposób:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Żadna z `ObjectID` wartości przekazywane przez `MovedReferences` obowiązują podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w środku przenoszenie obiektów z starego lokalizacji do nowej lokalizacji. W związku z tym profilery nie powinny podejmować próby sprawdź obiekty podczas `MovedReferences` wywołania. A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego wskazuje, że wszystkie obiekty zostały przeniesione do nowej lokalizacji i inspekcji mogą być wykonywane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [MovedReferences2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
