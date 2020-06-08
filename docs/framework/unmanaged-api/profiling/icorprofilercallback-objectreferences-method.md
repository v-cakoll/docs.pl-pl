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
ms.openlocfilehash: 12a0792e8fafc73b480de6bacc86f98470dfedf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503292"
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
 podczas Liczba obiektów przywoływanych przez określony obiekt (czyli liczba elementów w `objectRefIds` tablicy).  
  
 `objectRefIds`  
 podczas Tablica identyfikatorów obiektów, do których odwołuje się `objectId` .  
  
## <a name="remarks"></a>Uwagi  
 `ObjectReferences`Metoda jest wywoływana dla każdego obiektu pozostałego w stercie po zakończeniu odzyskiwania pamięci. Jeśli profiler zwróci błąd z tego wywołania zwrotnego, usługi profilowania będą kontynuowały wywoływanie tego wywołania zwrotnego do momentu kolejnego wyrzucania elementów bezużytecznych.  
  
 `ObjectReferences`Wywołania zwrotnego można użyć w połączeniu z wywołaniem zwrotnym [ICorProfilerCallback:: RootReferences —](icorprofilercallback-rootreferences-method.md) w celu utworzenia kompletnego grafu odwołań do obiektów dla środowiska uruchomieniowego. Środowisko uruchomieniowe języka wspólnego (CLR) gwarantuje, że każde odwołanie do obiektu jest raportowane tylko raz przez `ObjectReferences` metodę.  
  
 Identyfikatory obiektów zwrócone przez `ObjectReferences` nie są prawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w trakcie przesuwania obiektów. W związku z tym, nie mogą próbować zbadać obiektów podczas `ObjectReferences` wywołania. Gdy wywoływana jest [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) , odzyskiwanie pamięci jest kompletne i można bezpiecznie wykonać inspekcję.  
  
 Wartość null `ClassId` wskazuje `objectId` Typ, który jest wyładowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
