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
ms.openlocfilehash: 38d9e83e9fa0e9cd0586fb10a6fd79c29bead4a6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866107"
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
 Metoda `ObjectedAllocated` nie jest wywoływana dla alokacji z pamięci stosu lub niezarządzanej. Parametr `classId` może odwoływać się do klasy w zarządzanym kodzie, który nie został jeszcze załadowany. Profiler otrzyma wywołanie zwrotne ładowania klasy dla tej klasy natychmiast po wywołaniu wywołania zwrotnego `ObjectAllocated`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [ClassLoadStarted, metoda](icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished, metoda](icorprofilercallback-classloadfinished-method.md)
