---
title: "ICorProfilerCallback::RuntimeSuspendFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6127d0c5f3b193dad1586cdaf92beb8d8734376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a>ICorProfilerCallback::RuntimeSuspendFinished — Metoda
Powiadamia profilera, czy środowisko uruchomieniowe zostało zakończone zawieszenia wszystkie wątki środowiska wykonawczego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wątki środowiska uruchomieniowego należących do kodu niezarządzanego, mogą nadal działać do chwili próbują ponownie wprowadzić środowiska uruchomieniowego. W tym momencie one zostaną również zawieszone, dopóki nie zostanie wznowione środowiska uruchomieniowego. Dotyczy to również nowy wątków, które należy wprowadzić środowiska uruchomieniowego. Wszystkie wątki w środowisku uruchomieniowym są albo zawieszone natychmiast, jeśli są one już przerywania kodu lub użytkownicy zostaną poproszeni o zawiesić po upływie przerywania kodu.  
  
 `RuntimeSuspendFinished` Wywołania zwrotnego jest gwarantowana występuje w tym samym wątku, co [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [RuntimeSuspendAborted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
