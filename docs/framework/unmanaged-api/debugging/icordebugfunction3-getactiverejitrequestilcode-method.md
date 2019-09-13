---
title: Metoda ICorDebugFunction3::GetActiveReJitRequestILCode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4985a448321eceabf7975a8e5b638043f6c88723
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926854"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>Metoda ICorDebugFunction3::GetActiveReJitRequestILCode
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wskaźnik interfejsu do [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) zawierającego Il z aktywnego żądania ReJIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppReJitedILCode`  
 Wskaźnik do IL z aktywnego żądania ReJIT.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda reprezentowana przez ten `ICorDebugFunction3` obiekt ma aktywne żądanie ReJIT, `ppReJitedILCode` zwraca wskaźnik do jego Il. Jeśli nie ma aktywnych żądań, które są typowym przypadkiem, wówczas `ppReJitedILCode` ma **wartość null**.  
  
 Żądanie ReJIT jest uaktywniane tuż po powrocie wykonania z wywołania metody [ICorProfilerCallback4:: GetReJITParameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) . Może nie być jeszcze skompilowana w trybie JIT, a wątki nadal mogą być wykonywane w pierwotnej wersji kodu. Żądanie ReJIT stanie się nieaktywne w trakcie wywołania profilera do metody [ICorProfilerInfo4:: RequestRevert —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) . Nawet po przywróceniu kodu IL wątek nadal może być wykonywany w kodzie JIT-rekompilowanym (ReJIT).  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugFunction3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Przewodnik krok po kroku](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
