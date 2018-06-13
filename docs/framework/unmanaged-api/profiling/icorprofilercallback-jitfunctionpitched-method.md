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
ms.openlocfilehash: cf51d2a0e7381cd495da8f3846302ec806c34774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451415"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>ICorProfilerCallback::JITFunctionPitched — Metoda
Powiadamia profilera który funkcja, która została just-in-time (JIT)-skompilowany został usunięty z pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, która została usunięta.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli usunięto funkcja jest wywoływana, profilera otrzymają nowe zdarzenia kompilacji JIT, gdy funkcja jest ponownie kompilowana. Obecnie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) przy użyciu kompilatora JIT nie powoduje usunięcia funkcji z pamięci, dzięki czemu to wywołanie zwrotne nie jest obecnie używana i nie zostanie odebrana przez profiler.  
  
 Wartość `functionId` jest nieprawidłowa, dopóki funkcja jest ponownie kompilowana. Gdy funkcja jest ponownie kompilowana, takie same `functionId` zostanie użyta wartość.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
