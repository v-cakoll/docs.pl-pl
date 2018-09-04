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
ms.openlocfilehash: c49a9543c7bfeb9882144fba74b9c48cfba64890
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519354"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>Metoda ICorDebugFunction3::GetActiveReJitRequestILCode
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wskaźnik interfejsu do [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) zawierający IL z aktywne żądanie ReJIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppReJitedILCode`  
 Wskaźnik do IL od aktywne żądanie ReJIT.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda reprezentowany przez ten `ICorDebugFunction3` obiekt ma aktywne żądanie ReJIT `ppReJitedILCode` zwraca wskaźnik do jego IL. Jeśli nie istnieje żadne aktywne żądanie, który jest przypadkiem typowe `ppReJitedILCode` jest **null**.  
  
 Żądanie ReJIT staje się aktywny po wykonywanie powraca z [icorprofilercallback4::getrejitparameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania metody. Nie może jeszcze być kompilowany dokładnie na czas i wątki nadal mogą być wykonywane w pierwotnej wersji kodu. Żądanie ReJIT staje się nieaktywny podczas wywoływania programu profilującego [icorprofilerinfo4::requestrevert —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metody. Nawet po zakończeniu przywróconych IL to wątek może nadal wykonywane w kodzie ponownie skompilowana JIT (ReJIT).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugFunction3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Przewodnik](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
