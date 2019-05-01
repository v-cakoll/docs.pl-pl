---
title: ICorProfilerCallback2::RootReferences2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09616243aef272be041573864effd25017cc65c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992033"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 — Metoda
Powiadamia program profilujący o odwołaniach do katalogu głównego, po przeprowadzeniu wyrzucania elementów bezużytecznych. Ta metoda jest rozszerzeniem [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [in] Liczba elementów w `rootRefIds`, `rootKinds`, `rootFlags`, i `rootIds` tablic.  
  
 `rootRefIds`  
 [in] Tablica obiektów identyfikatorów, każdy z nich odwołuje się do obiektu statycznego lub obiekt na stosie. Elementy w `rootKinds` tablicy Podaj informacje potrzebne do klasyfikowania odpowiednie elementy w `rootRefIds` tablicy.  
  
 `rootKinds`  
 [in] Tablica [cor_prf_gc_root_kind —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) wartości, które wskazują na typ główny kolekcji wyrzucania elementów.  
  
 `rootFlags`  
 [in] Tablica [cor_prf_gc_root_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) wartości, które opisują właściwości głównego kolekcji wyrzucania elementów.  
  
 `rootIds`  
 [in] Tablica UINT_PTR wartości tego punktu na liczbę całkowitą, która zawiera dodatkowe informacje na temat głównych kolekcji wyrzucania elementów, w zależności od wartości `rootKinds` parametru.  
  
 Jeśli typ główny jest stos, identyfikator katalogu głównego jest dla funkcji, która zawiera zmienną. Jeśli ten identyfikator główny wynosi 0, funkcja jest bez nazwy funkcji, która jest wewnętrzny środowiska CLR. Jeśli typ główny jest uchwytem, identyfikator katalogu głównego wynosi uchwyt kolekcji wyrzucania elementów. Dla innych typów głównego Identyfikatora jest nieprzezroczysta wartość i należy ją ignorować.  
  
## <a name="remarks"></a>Uwagi  
 `rootRefIds`, `rootKinds`, `rootFlags`, I `rootIds` tablic są tablicami równoległych. Oznacza to, że `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, i `rootIds[i]` dotyczą wszystkich takim samym certyfikatem głównym.  
  
 Zarówno `RootReferences` i `RootReferences2` są wywoływane w celu powiadomić profiler. Profilery zwykle wdroży jednej lub drugiej metody, ale nie obie, ponieważ informacje są przekazywane w `RootReferences2` jest nadzbiorem, przekazanej `RootReferences`.  
  
 Istnieje możliwość, że wpisy w `rootRefIds` zero, co oznacza, że główny odwołań ma wartość null i nie odwołuje się do obiektu w zarządzanym stosie.  
  
 Identyfikatory obiektów są zwracane przez `RootReferences2` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucania elementów bezużytecznych może być w trakcie przenoszenia obiektów z stare adresy do nowych adresów. W związku z tym, profilowania nie należy próbować Zbadaj obiekty podczas `RootReferences2` wywołania. Gdy [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i może być bezpiecznie kontrolowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
