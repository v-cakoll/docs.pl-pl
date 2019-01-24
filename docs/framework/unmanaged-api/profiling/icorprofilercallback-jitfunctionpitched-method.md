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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91bc626e2c75cd7eb2eafad0fc26d343e5b278e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530735"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>ICorProfilerCallback::JITFunctionPitched — Metoda
Powiadamia program profilujący, że funkcja, która została just-in-time (JIT) — skompilowany został usunięty z pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, która została usunięta.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli usunięto funkcja jest wywoływana, program profilujący otrzyma nowe zdarzenia kompilacji JIT, gdy funkcja jest ponownie kompilowana. Obecnie kompilator JIT języka wspólnego środowiska uruchomieniowego (języka wspólnego CLR) nie powoduje usunięcia funkcji z pamięci, dzięki czemu to wywołanie zwrotne nie jest obecnie używana i nie będą odbierane przez profiler.  
  
 Wartość `functionId` jest nieprawidłowa, dopóki funkcja jest ponownie kompilowana. Gdy funkcja jest ponownie kompilowany, taka sama `functionId` zostanie użyta wartość.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
