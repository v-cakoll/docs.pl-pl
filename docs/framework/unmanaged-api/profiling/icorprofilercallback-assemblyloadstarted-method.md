---
title: ICorProfilerCallback::AssemblyLoadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: deb8475ab338c6ce733f1700e509dff982bd697f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611179"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a>ICorProfilerCallback::AssemblyLoadStarted — Metoda
Powiadamia program profilujący, że zestaw jest ładowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `assemblyId`  
 [in] Określa zestaw, który jest ładowany.  
  
## <a name="remarks"></a>Uwagi  
 Wartość `assemblyId` jest nieprawidłowa dla żądania informacje do momentu [icorprofilercallback::assemblyloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) metoda jest wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
