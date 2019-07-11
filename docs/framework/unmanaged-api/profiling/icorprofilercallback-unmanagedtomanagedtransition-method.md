---
title: ICorProfilerCallback::UnmanagedToManagedTransition — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fa7dfe101b07ae6eb8d58daad85954f0ce29b02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747058"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition — Metoda
Powiadamia program profilujący, że nastąpiło przejście z niezarządzanego kodu do kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, która jest wywoływana.  
  
 `reason`  
 [in] Wartość [cor_prf_transition_reason —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) wyliczenia, która wskazuje, czy przejście wystąpiły z powodu wywołanie kodu zarządzanego z niezarządzanego kodu lub ze względu na powrót z funkcji niezarządzanej wywoływana przez zarządzane.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `reason` jest COR_PRF_TRANSITION_RETURN i `functionId` jest nie jest to null, funkcja identyfikator jest to, że funkcji niezarządzanych i będzie nigdy nie zostały skompilowane przy użyciu kompilatora just-in-time (JIT). Niezarządzane funkcje ma niektórych podstawowych informacji z nimi związane, takie jak nazwa i niektóre metadane.  
  
 Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, jest możliwe, że funkcja o nazwie (czyli funkcji zarządzanej) nie została jeszcze kompilowany dokładnie na czas.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ManagedToUnmanagedTransition, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
