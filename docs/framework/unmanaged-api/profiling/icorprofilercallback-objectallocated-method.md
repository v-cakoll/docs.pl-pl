---
title: ICorProfilerCallback::ObjectAllocated — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: 9a402b7dfc3ece9d38994ed897162fe0d81ff0b9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503305"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated — Metoda
Powiadamia program profilujący, że pamięć w stercie została przypisana dla obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 podczas Identyfikator obiektu, dla którego przydzielono pamięć.  
  
 `classId`  
 podczas Identyfikator klasy, której obiekt jest wystąpieniem.  
  
## <a name="remarks"></a>Uwagi  
 `ObjectedAllocated`Metoda nie jest wywoływana dla alokacji z pamięci stosu lub niezarządzanej. `classId`Parametr może odwoływać się do klasy w zarządzanym kodzie, który nie został jeszcze załadowany. Profiler otrzyma wywołanie zwrotne ładowania klasy dla tej klasy bezpośrednio po `ObjectAllocated` wywołaniu zwrotnym.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ClassLoadStarted, metoda](icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished, metoda](icorprofilercallback-classloadfinished-method.md)
