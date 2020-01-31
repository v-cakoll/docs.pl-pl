---
title: ICorProfilerCallback::ManagedToUnmanagedTransition — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: 0750ac66c654285e11dbbb5941f029bf5f900842
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866198"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition — Metoda
Powiadamia profiler o wystąpieniu przejścia z kodu zarządzanego do kodu niezarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, która jest wywoływana.  
  
 `reason`  
 podczas Wartość wyliczenia [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) , która wskazuje, czy przejście wystąpiło z powodu wywołania do niezarządzanego kodu z kodu zarządzanego lub z powodu powrotu z funkcji zarządzanej wywołanej przez niezarządzaną metodę.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, identyfikator funkcji jest niezarządzaną funkcją, która nigdy nie została skompilowana przy użyciu kompilatora just in Time. Z niezarządzanymi funkcjami są skojarzone podstawowe informacje, takie jak nazwa i niektóre metadane. Jeśli funkcja niezarządzana została wywołana przy użyciu niejawnego wywołania platformy (PInvoke), środowisko uruchomieniowe nie może ustalić miejsca docelowego wywołania i wartość `functionId` będzie równa null. Aby uzyskać więcej informacji na temat niejawnego elementu PInvoke, zobacz [ C++ using Interop (niejawne PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition, metoda](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
