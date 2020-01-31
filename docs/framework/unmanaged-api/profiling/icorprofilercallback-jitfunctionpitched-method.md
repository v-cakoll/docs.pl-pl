---
title: ICorProfilerCallback::JITFunctionPitched — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: cda629b7a6560ca5d731cd88cffc2cffd3486d8a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866224"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>ICorProfilerCallback::JITFunctionPitched — Metoda
Powiadamia program profilujący, że funkcja, która została skompilowana just-in-Time (JIT), została usunięta z pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, która została usunięta.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli usunięta funkcja zostanie wywołana, profiler otrzyma nowe zdarzenia JIT-kompilacja po ponownym skompilowaniu funkcji. Obecnie kompilator JIT środowiska uruchomieniowego języka wspólnego (CLR) nie usuwa funkcji z pamięci, więc to wywołanie zwrotne nie jest obecnie używane i nie zostanie odebrane przez profiler.  
  
 Wartość `functionId` jest nieprawidłowa do momentu ponownego skompilowania funkcji. Po ponownym skompilowaniu funkcji zostanie użyta ta sama wartość `functionId`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
