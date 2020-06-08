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
ms.openlocfilehash: 2ce58113f40c8eb67a89b6ab6c9bb8f755975bd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499756"
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
 podczas Liczba elementów w `rootRefIds` tablicach,, `rootKinds` `rootFlags` i `rootIds` .  
  
 `rootRefIds`  
 podczas Tablica identyfikatorów obiektów, z których każdy odwołuje się do obiektu statycznego lub obiektu na stosie. Elementy w `rootKinds` tablicy zawierają informacje do klasyfikowania odpowiadających im elementów w `rootRefIds` tablicy.  
  
 `rootKinds`  
 podczas Tablica wartości [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) , które wskazują typ elementu głównego wyrzucania elementów bezużytecznych.  
  
 `rootFlags`  
 podczas Tablica wartości [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) , które opisują właściwości katalogu głównego wyrzucania elementów bezużytecznych.  
  
 `rootIds`  
 podczas Tablica wartości UINT_PTR, która wskazuje liczbę całkowitą, która zawiera dodatkowe informacje o katalogu głównym wyrzucania elementów bezużytecznych, w zależności od wartości `rootKinds` parametru.  
  
 Jeśli typ elementu głównego to stos, identyfikator główny jest dla funkcji, która zawiera zmienną. Jeśli ten identyfikator główny to 0, funkcja jest nienazwaną funkcją, która jest wewnętrzna dla środowiska CLR. Jeśli typ elementu głównego to dojście, identyfikator główny jest dla dojścia do wyrzucania elementów bezużytecznych. W przypadku innych typów głównych identyfikator jest wartością nieprzezroczystą i powinien zostać zignorowany.  
  
## <a name="remarks"></a>Uwagi  
 `rootRefIds`Tablice, `rootKinds` , `rootFlags` i `rootIds` są tablicami równoległymi. To jest,,, `rootRefIds[i]` `rootKinds[i]` `rootFlags[i]` i `rootIds[i]` wszystko dotyczy tego samego katalogu głównego.  
  
 Oba `RootReferences` i `RootReferences2` są wywoływane w celu powiadomienia profilera. Profilowający zwykle implementują jedną metodę lub drugą, ale nie obie, ponieważ przesyłane informacje `RootReferences2` są podzbiorem, który przeszedł `RootReferences` .  
  
 Istnieje możliwość, że wpisy w `rootRefIds` wartości są równe zero, co oznacza, że odpowiadające mu odwołanie główne ma wartość null i nie odwołuje się do obiektu w zarządzanym stosie.  
  
 Identyfikatory obiektów zwrócone przez `RootReferences2` nie są prawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może być w trakcie przeniesienia obiektów ze starych adresów na nowe adresy. W związku z tym nie należy próbować kontrolować obiektów podczas `RootReferences2` wywołania. Gdy wywoływana jest [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) , wszystkie obiekty zostały przeniesione do nowych lokalizacji i można je bezpiecznie sprawdzić.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 — Interfejs](icorprofilercallback2-interface.md)
