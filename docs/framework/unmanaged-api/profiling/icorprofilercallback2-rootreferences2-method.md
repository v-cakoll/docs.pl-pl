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
ms.openlocfilehash: a9ce9a7a56847efcadf09924ffc56c41f20a1c58
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865730"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 — Metoda
Powiadamia profiler o odwołaniach głównych po wystąpieniu wyrzucania elementów bezużytecznych. Ta metoda jest rozszerzeniem metody [ICorProfilerCallback:: RootReferences —](icorprofilercallback-rootreferences-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cRootRefs`  
 podczas Liczba elementów w tablicach `rootRefIds`, `rootKinds`, `rootFlags`i `rootIds`.  
  
 `rootRefIds`  
 podczas Tablica identyfikatorów obiektów, z których każdy odwołuje się do obiektu statycznego lub obiektu na stosie. Elementy w tablicy `rootKinds` zawierają informacje do klasyfikowania odpowiadających im elementów w tablicy `rootRefIds`.  
  
 `rootKinds`  
 podczas Tablica wartości [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) , które wskazują typ elementu głównego wyrzucania elementów bezużytecznych.  
  
 `rootFlags`  
 podczas Tablica wartości [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) , które opisują właściwości katalogu głównego wyrzucania elementów bezużytecznych.  
  
 `rootIds`  
 podczas Tablica wartości UINT_PTR, która wskazuje liczbę całkowitą, która zawiera dodatkowe informacje o katalogu głównym wyrzucania elementów bezużytecznych, w zależności od wartości parametru `rootKinds`.  
  
 Jeśli typ elementu głównego to stos, identyfikator główny jest dla funkcji, która zawiera zmienną. Jeśli ten identyfikator główny to 0, funkcja jest nienazwaną funkcją, która jest wewnętrzna dla środowiska CLR. Jeśli typ elementu głównego to dojście, identyfikator główny jest dla dojścia do wyrzucania elementów bezużytecznych. W przypadku innych typów głównych identyfikator jest wartością nieprzezroczystą i powinien zostać zignorowany.  
  
## <a name="remarks"></a>Uwagi  
 Tablice `rootRefIds`, `rootKinds`, `rootFlags`i `rootIds` są tablicami równoległymi. Oznacza to, że `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`i `rootIds[i]` wszystkie dotyczą tego samego katalogu głównego.  
  
 Obie `RootReferences` i `RootReferences2` są wywoływane w celu powiadomienia profilera. Obiekty profilowające zwykle implementują jedną metodę lub drugą, ale nie obie, ponieważ informacje przesyłane `RootReferences2` są nadzbiorem, który przeszedł `RootReferences`.  
  
 Możliwe jest, aby wpisy w `rootRefIds` miały wartość zero, co oznacza, że odpowiadające mu odwołanie główne ma wartość null i nie odwołuje się do obiektu na stercie zarządzanym.  
  
 Identyfikatory obiektów zwrócone przez `RootReferences2` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może być w trakcie przeniesienia obiektów ze starych adresów na nowe adresy. W związku z tym nie należy próbować kontrolować obiektów podczas wywołania `RootReferences2`. Gdy wywoływana jest [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) , wszystkie obiekty zostały przeniesione do nowych lokalizacji i można je bezpiecznie sprawdzić.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](icorprofilercallback2-interface.md)
