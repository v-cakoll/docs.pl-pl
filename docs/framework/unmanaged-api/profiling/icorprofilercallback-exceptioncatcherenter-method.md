---
title: ICorProfilerCallback::ExceptionCatcherEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 534e0672820cc2509f32765274ad970fda69ec5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866510"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter — Metoda
Powiadamia profiler, że sterowanie jest przesyłane do odpowiedniego bloku `catch`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>Parametry

- `functionId`

  \[in) identyfikator funkcji zawierającej blok `catch`.
  
- `objectId`

  \[w] Identyfikator obsługiwanego wyjątku.

## <a name="remarks"></a>Uwagi  
 Metoda `ExceptionCatcherEnter` jest wywoływana tylko wtedy, gdy punkt catch jest w kodzie skompilowanym za pomocą kompilatora just-in-Time (JIT). Wyjątek przechwytywany w kodzie niezarządzanym lub w kodzie wewnętrznym środowiska uruchomieniowego nie wywoła tego powiadomienia. Wartość `objectId` jest przenoszona ponownie, ponieważ wyrzucanie elementów bezużytecznych mogło przenieść obiekt od momentu powiadomienia `ExceptionThrown`.  
  
 Profiler nie powinien blokować swojej implementacji tej metody, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych i dlatego nie można włączyć zastępujący elementów bezużytecznych. Jeśli profiler blokuje tutaj i zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.  
  
 Implementacja profilera nie powinna być wywoływana w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [ExceptionCatcherLeave, metoda](icorprofilercallback-exceptioncatcherleave-method.md)
