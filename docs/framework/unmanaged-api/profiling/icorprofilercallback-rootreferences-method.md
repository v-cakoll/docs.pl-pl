---
title: ICorProfilerCallback::RootReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: 948628f469eecabfbbe792dcc3edf2e1204ffc36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865964"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences — Metoda
Powiadamia profiler o informacji o odwołaniach głównych po wyrzucaniu elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cRootRefs`  
 podczas Liczba odwołań w tablicy `rootRefIds`.  
  
 `rootRefIds`  
 podczas Tablica identyfikatorów obiektów odwołujących się do obiektu statycznego lub obiektu na stosie.  
  
## <a name="remarks"></a>Uwagi  
 Elementy `RootReferences` i [ICorProfilerCallback2:: RootReferences2 —](icorprofilercallback2-rootreferences2-method.md) są wywoływane w celu powiadomienia profilera. Obiekty profilowające zwykle implementują jeden lub drugi, ale nie obie, ponieważ informacje przesyłane `RootReferences2` są nadzbiorem, który przeszedł `RootReferences`.  
  
 Istnieje możliwość, aby tablica `rootRefIds` zawierała obiekt o wartości null. Na przykład wszystkie odwołania do obiektów zadeklarowane na stosie są traktowane jako elementy główne przez moduł wyrzucania elementów bezużytecznych i zawsze będą raportowane.  
  
 Identyfikatory obiektów zwrócone przez `RootReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może być w trakcie przeniesienia obiektów ze starych adresów na nowe adresy. W związku z tym, nie mogą próbować zbadać obiektów podczas wywołania `RootReferences`. Gdy wywoływana jest [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) , wszystkie obiekty zostały przeniesione do nowych lokalizacji i można je bezpiecznie sprawdzić.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
