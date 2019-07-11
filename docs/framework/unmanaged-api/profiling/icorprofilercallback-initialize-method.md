---
title: ICorProfilerCallback::Initialize — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e50421dc15dd30f1811dbe5ebef2ff2f7a0a9483
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755823"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize — Metoda
Wywoływane w celu zainicjowania programu profilującego kodu, przy każdym uruchomieniu typowych aplikacji środowiska uruchomieniowego (języka wspólnego CLR) języka.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `pICorProfilerInfoUnk`  
 [w](/cpp/atl/iunknown) interfejs, który program profilujący musi szukać [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) wskaźnika interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 `Initialize` Wywołanie jest tylko szansy sprzedaży, aby włączyć (lub wyłączyć) wywołania zwrotne, które są niezmienne. Po włączeniu wywołanie zwrotne przez `Initialize` wywoływać, nie można wyłączyć, używając [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Wartość COR_PRF_MONITOR_IMMUTABLE [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia wskazuje, jakie zdarzenia są niezmienne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Shutdown, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
