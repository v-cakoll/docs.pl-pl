---
title: ICorProfilerCallback::ExceptionOSHandlerEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7842e7a8f12a58aa56fd5be5674b183fc515f51b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608456"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a>ICorProfilerCallback::ExceptionOSHandlerEnter — Metoda
Nie zaimplementowano. Profiler, który potrzebuje informacji niezarządzany wyjątek, należy uzyskać te informacje w inny sposób.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
