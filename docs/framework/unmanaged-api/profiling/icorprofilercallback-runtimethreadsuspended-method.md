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
ms.openlocfilehash: 7673d6fac2626bc0059204ea77a23686b11638cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452738"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended — Metoda
Powiadamia profilera, czy określony wątek został wstrzymany lub ma zostać zawieszone.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 [in] Identyfikator wątku, który został wstrzymany.  
  
## <a name="remarks"></a>Uwagi  
 `RuntimeThreadSuspended` Powiadomień może wystąpić w dowolnej chwili między [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) oraz skojarzonych z nimi [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołań zwrotnych. Powiadomienia, które mają miejsce między [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i `RuntimeResumeStarted` dla wątków, które były uruchomione w niezarządzanych kodu i konto zostało zawieszone po ich wprowadzeniu do środowiska wykonawczego.  
  
 Ogólnie rzecz biorąc to wywołanie zwrotne występuje tuż po wątek jest zawieszony. Jeśli aktualnie wykonywane wątku (wątek tego wywołania zwrotnego wywoływana) jest ten, który jest wstrzymywane, to wywołanie zwrotne odbywa się jednak tuż przed wątek jest zawieszony.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [RuntimeThreadResumed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
