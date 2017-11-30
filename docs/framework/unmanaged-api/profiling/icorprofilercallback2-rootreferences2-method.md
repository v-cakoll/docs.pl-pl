---
title: "ICorProfilerCallback2::RootReferences2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.RootReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a0b2e23ba586e7a20ed11de6433b2d87cbe7219
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 — Metoda
Powiadamia profilera odwołania głównego informacje po zakończeniu wyrzucania elementów bezużytecznych. Ta metoda jest rozszerzeniem [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [in] Liczba elementów w `rootRefIds`, `rootKinds`, `rootFlags`, i `rootIds` tablic.  
  
 `rootRefIds`  
 [in] Tablica obiektów identyfikatorów, które odwołuje się do statycznego obiektu albo obiekt na stosie. Elementy w `rootKinds` tablicy zawierają informacje do klasyfikowania odpowiednich elementów w `rootRefIds` tablicy.  
  
 `rootKinds`  
 [in] Tablica [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) wartości, które wskazują na typ główny kolekcji pamięci.  
  
 `rootFlags`  
 [in] Tablica [cor_prf_gc_root_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) wartości, które opisują właściwości głównego kolekcji pamięci.  
  
 `rootIds`  
 [in] Tablica UINT_PTR wartości prowadzące do liczba całkowita, która zawiera dodatkowe informacje dotyczące głównego kolekcji odzyskiwanie, w zależności od wartości `rootKinds` parametru.  
  
 Jeśli typ główny stos, identyfikator katalogu głównego jest dla tej funkcji, która zawiera zmienną. Jeśli ten identyfikator głównego to 0, ta funkcja jest bez nazwy funkcji, która jest wewnętrzny do środowiska CLR. Jeśli typu głównego uchwytu, identyfikator katalogu głównego jest na dojście kolekcji pamięci. Dla innych typów głównego Identyfikatora jest wartości nieprzezroczystej i należy ją ignorować.  
  
## <a name="remarks"></a>Uwagi  
 `rootRefIds`, `rootKinds`, `rootFlags`, I `rootIds` tablice są tablice równoległych. Oznacza to `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, i `rootIds[i]` wszystkie dotyczą tego samego głównego.  
  
 Zarówno `RootReferences` i `RootReferences2` są wywoływane w celu powiadomienia profilera. Profilery będzie zwykle implementowany jednej lub drugiej metody, ale nie oba ponieważ przekazane informacje `RootReferences2` jest nadzbiorem tego przekazano `RootReferences`.  
  
 Istnieje możliwość wpisów w `rootRefIds` zero, co oznacza, że odwołanie do odpowiedniego katalogu głównego ma wartość null i nie odwołuje się do obiektu na stercie zarządzanej.  
  
 Identyfikatory obiektów zwrócona przez `RootReferences2` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w środku przenoszenie obiektów z stare adresy do nowych adresów. W związku z tym profilery nie powinny podejmować próby sprawdź obiekty podczas `RootReferences2` wywołania. Gdy [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wszystkie obiekty zostały przeniesione do nowej lokalizacji i może być bezpiecznie kontrolowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
