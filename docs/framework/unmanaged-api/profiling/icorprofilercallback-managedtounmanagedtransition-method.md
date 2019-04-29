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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b00394d0b08e7e4a02b95437908dd65a51d0a042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597677"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition — Metoda
Powiadamia program profilujący, że nastąpiło przejście z kodu zarządzanego do kodu niezarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, która jest wywoływana.  
  
 `reason`  
 [in] Wartość [cor_prf_transition_reason —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) wyliczenia, która wskazuje, czy przejście wystąpiły z powodu wywołania kodu niezarządzanego z kodu zarządzanego lub ze względu na powrót z funkcji zarządzanej wywoływane przez jeden z niezarządzanego.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, funkcja identyfikator to, że funkcji niezarządzanych, który będzie nigdy nie zostały skompilowane przy użyciu kompilatora just-in-time. Funkcje niezarządzane mają podstawowe informacje z nimi związane, takie jak nazwa i niektóre metadane. Jeśli niezarządzane funkcja została wywołana przy użyciu platformy niejawne wywołania (funkcja PInvoke), środowisko uruchomieniowe nie może określić docelową wywołania i wartości `functionId` będzie miał wartość null. Aby uzyskać więcej informacji na temat niejawna funkcja PInvoke, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
