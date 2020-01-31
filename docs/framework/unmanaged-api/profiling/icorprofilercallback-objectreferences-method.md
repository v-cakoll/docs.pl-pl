---
title: ICorProfilerCallback::ObjectReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 6e6cc44c2f9028c0e26c4f933242cad93e3a98c3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866094"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences — Metoda
Powiadamia profiler o obiektach w pamięci, do których odwołuje się określony obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 podczas Identyfikator obiektu, który odwołuje się do obiektów.  
  
 `classId`  
 podczas Identyfikator klasy, do której należy wystąpienie określonego obiektu.  
  
 `cObjectRefs`  
 podczas Liczba obiektów przywoływanych przez określony obiekt (czyli liczba elementów w tablicy `objectRefIds`).  
  
 `objectRefIds`  
 podczas Tablica identyfikatorów obiektów, do których odwołują się `objectId`.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `ObjectReferences` jest wywoływana dla każdego obiektu pozostałego w stercie po zakończeniu odzyskiwania pamięci. Jeśli profiler zwróci błąd z tego wywołania zwrotnego, usługi profilowania będą kontynuowały wywoływanie tego wywołania zwrotnego do momentu kolejnego wyrzucania elementów bezużytecznych.  
  
 Wywołania zwrotnego `ObjectReferences` można użyć w połączeniu z wywołaniem zwrotnym [ICorProfilerCallback:: RootReferences —](icorprofilercallback-rootreferences-method.md) w celu utworzenia kompletnego grafu odwołań do obiektów dla środowiska uruchomieniowego. Środowisko uruchomieniowe języka wspólnego (CLR) gwarantuje, że każde odwołanie do obiektu jest raportowane tylko raz przez metodę `ObjectReferences`.  
  
 Identyfikatory obiektów zwrócone przez `ObjectReferences` nie są prawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w trakcie przesuwania obiektów. W związku z tym, nie mogą próbować zbadać obiektów podczas wywołania `ObjectReferences`. Gdy wywoływana jest [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) , odzyskiwanie pamięci jest kompletne i można bezpiecznie wykonać inspekcję.  
  
 `ClassId` o wartości null wskazuje, że `objectId` ma typ, który jest wyładowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
