---
title: Metoda ICorDebugFunction3::GetActiveReJitRequestILCode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugFunction3.GetActiveReJitRequestILCode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae041a9a5973194398bbfed41771396b305f52fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>Metoda ICorDebugFunction3::GetActiveReJitRequestILCode
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wskaźnika interfejsu do [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) zawierający IL z aktywne żądanie ReJIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppReJitedILCode`  
 Wskaźnik do IL z aktywne żądanie ReJIT.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda reprezentowany przez to `ICorDebugFunction3` obiekt ma aktywne żądanie ReJIT `ppReJitedILCode` zwraca wskaźnik do jego IL. Jeśli nie istnieje żadne aktywne żądanie, który jest następnie typowych przypadkach, `ppReJitedILCode` jest **null**.  
  
 Żądanie ReJIT staje się aktywny tuż po wykonywania zwraca z [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania metody. Nie może jeszcze być skompilowany JIT i wątków nadal mogą być wykonywane w oryginalnej wersji kodu. Żądanie ReJIT staje się nieaktywny podczas wywołania profilera [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metody. Nawet po IL zostanie przywrócony, wątek nadal można wykonywane w kodzie ponownie kompilowana JIT (ReJIT).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugFunction3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Przewodnik](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
