---
title: ICorDebugThread, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1517d686c50923f5599e33436e0ad6126e8be140
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923142"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread, interfejs
Reprezentuje wątek w procesie. Okres istnienia `ICorDebugThread` wystąpienia jest taki sam jak okres istnienia wątku, który reprezentuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearCurrentException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Ta metoda nie jest zaimplementowana. Nie używaj go.|  
|[CreateEval, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Tworzy obiekt ICorDebugEval, który działa na tym `ICorDebugThread`.|  
|[CreateStepper, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Tworzy obiekt ICorDebugStepper, który umożliwia przechodzenie przez aktywną ramkę `ICorDebugThread`w tym elemencie.|  
|[EnumerateChains, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu `ICorDebugThread`w tym elemencie.|  
|[GetActiveChain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Pobiera wskaźnik interfejsu do aktywnego ICorDebugChain `ICorDebugThread`.|  
|[GetActiveFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Pobiera wskaźnik interfejsu do aktywnego ICorDebugFrame `ICorDebugThread`.|  
|[GetAppDomain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Pobiera wskaźnik interfejsu do domeny aplikacji, w której `ICorDebugThread` jest aktualnie wykonywany.|  
|[GetCurrentException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek, który jest aktualnie generowany przez kod zarządzany.|  
|[GetDebugState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Pobiera wartość CorDebugThreadState —, która opisuje bieżący stan debugowania tego `ICorDebugThread`elementu.|  
|[GetHandle, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Pobiera bieżące dojście dla aktywnej części tego `ICorDebugThread`elementu.|  
|[GetID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Pobiera bieżący identyfikator systemu operacyjnego aktywnej części tego `ICorDebugThread`elementu.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Pobiera wskaźnik interfejsu do wątku środowiska uruchomieniowego języka wspólnego (CLR).|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Pobiera wskaźnik interfejsu do procesu, którego częścią jest `ICorDebugThread` ten element.|  
|[GetRegisterSet, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Pobiera wskaźnik interfejsu do zestawu rejestru skojarzonego z tym `ICorDebugThread`elementem.|  
|[GetUserState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Pobiera bitową kombinację wartości CorDebugUserState —, które opisują bieżący stan tego `ICorDebugThread`elementu.|  
|[SetDebugState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Ustawia bitową kombinację `CorDebugThreadState` wartości opisujących stan debugowania tego `ICorDebugThread`elementu.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
