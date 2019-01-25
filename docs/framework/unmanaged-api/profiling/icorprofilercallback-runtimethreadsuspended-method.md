---
title: ICorProfilerCallback::RuntimeThreadSuspended — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb93dbf35501d44bb21d3d689aebeba3acd19f79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616810"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended — Metoda
Powiadamia program profilujący, że określony wątek zostało zawieszone lub ma zostać zawieszone.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 [in] Identyfikator wątku, który zostało zawieszone.  
  
## <a name="remarks"></a>Uwagi  
 `RuntimeThreadSuspended` Powiadomień mogą wystąpić w dowolnym czasie między [icorprofilercallback::runtimesuspendstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) oraz skojarzonych z nimi [icorprofilercallback::runtimeresumestarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołań zwrotnych. Powiadomienia, które mają miejsce między [icorprofilercallback::runtimesuspendfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i `RuntimeResumeStarted` dla wątków, które były uruchomione w kod niezarządzany i konto zostało zawieszone po wejściu do środowiska uruchomieniowego.  
  
 Ogólnie rzecz biorąc to wywołanie zwrotne występuje po wątek jest zawieszony. Jednak jeśli aktualnie wykonywany wątek (wątku, który wywołał to wywołanie zwrotne) jest tą, która jest wstrzymana, to wywołanie zwrotne wystąpi przed wątek jest zawieszony.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [RuntimeThreadResumed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
