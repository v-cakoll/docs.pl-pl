---
title: "ICorDebugController::Continue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Continue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6a96145801aa8ef6482e30e9c00b763d2501f36
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue — Metoda
Wznawia wykonywanie wątków zarządzanych po wywołaniu [Metoda Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fIsOutOfBand`  
 [in] Ustaw `true` Jeśli kontynuowanie ze zdarzenia poza pasmem; w przeciwnym razie wartość `false`.  
  
## <a name="remarks"></a>Uwagi  
 `Continue`kontynuuje proces po wywołaniu `ICorDebugController::Stop` metody.  
  
 Podczas debugowania w trybie mieszanym, nie należy wywoływać `Continue` na Win32 zdarzeń wątku, chyba że trwają ze zdarzenia poza pasmem.  
  
 *Zdarzeń wewnątrzpasmowe* zarządzanych zdarzeń lub normalne zdarzeń niezarządzane podczas którego debuger obsługuje interakcji z zarządzanego stan procesu. W takim przypadku odbiera debuger [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) wywołania zwrotnego z jego `fOutOfBand` ustawiono parametr `false`.  
  
 *Poza pasmem zdarzenia* jest zdarzeniem niezarządzany, podczas którego interakcji z zarządzanego stan procesu jest niemożliwe, gdy proces jest zatrzymana z powodu zdarzenia. W takim przypadku odbiera debuger `ICorDebugUnmanagedCallback::DebugEvent` wywołania zwrotnego z jego `fOutOfBand` ustawiono parametr `true`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
