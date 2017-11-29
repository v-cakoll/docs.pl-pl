---
title: "ICorProfilerCallback::ManagedToUnmanagedTransition — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ManagedToUnmanagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9da8dd44d5b87cd1c65b8b8837c9dd378039d332
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition — Metoda
Powiadamia profilera, że nastąpiło przejście z kodu zarządzanego do kodu niezarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, która jest wywoływana.  
  
 `reason`  
 [in] Wartość [cor_prf_transition_reason —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) wyliczenia, która wskazuje, czy przejście wystąpiły z powodu wywołania do kodu niezarządzanego z kodu zarządzanego lub ze względu na powrót z funkcją zarządzaną wywoływane przez jeden z niezarządzanych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, funkcja identyfikator jest, że niezarządzanych funkcji, która będzie nigdy nie zostały skompilowane przy użyciu kompilatora just in time. Funkcje niezarządzane mają podstawowe informacje skojarzone z nimi, takie jak nazwa i niektóre metadane. Jeśli niezarządzanej funkcji została wywołana przy użyciu platformy niejawne wywołania (PInvoke), środowisko uruchomieniowe nie może określić docelowy wywołania i wartość `functionId` będzie mieć wartość null. Aby uzyskać więcej informacji na niejawna funkcja PInvoke, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [UnmanagedToManagedTransition — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
