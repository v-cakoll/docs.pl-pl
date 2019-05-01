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
ms.openlocfilehash: db322bbdc7293410968542d0d22c572edb87795a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993983"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread, interfejs
Reprezentuje wątek w procesie. Okres istnienia `ICorDebugThread` wystąpienie jest taki sam, jak okres istnienia wątku, który reprezentuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearCurrentException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Ta metoda nie jest zaimplementowana. Nie używaj go.|  
|[CreateEval, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Tworzy obiekt ICorDebugEval, który działa na tym `ICorDebugThread`.|  
|[CreateStepper, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Tworzy obiekt ICorDebugStepper —, który umożliwia krokowe wykonywanie aktywnej ramki, w tym `ICorDebugThread`.|  
|[EnumerateChains, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Pobiera wskaźnik interfejsu do moduł wyliczający icordebugchainenum —, który zawiera wszystkie łańcuchów stosu, w tym `ICorDebugThread`.|  
|[GetActiveChain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Pobiera wskaźnik interfejsu do aktywnego icordebugchain — w tym `ICorDebugThread`.|  
|[GetActiveFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Pobiera wskaźnik interfejsu do aktywnego icordebugframe — w tym `ICorDebugThread`.|  
|[GetAppDomain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Pobiera wskaźnik interfejsu do domeny aplikacji, w którym znajduje się ten `ICorDebugThread` jest w trakcie wykonywania.|  
|[GetCurrentException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, która reprezentuje wyjątek zgłaszane przez kod zarządzany.|  
|[GetDebugState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Pobiera wartość cordebugthreadstate —, który opisuje bieżący stan debugowania tego `ICorDebugThread`.|  
|[GetHandle, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Pobiera bieżący uchwytu dla części active `ICorDebugThread`.|  
|[GetID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Pobiera identyfikator bieżącego systemu operacyjnego części active `ICorDebugThread`.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Pobiera wskaźnik interfejsu do wspólnym mianownikiem języka wspólnego (CLR).|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Pobiera wskaźnik interfejsu do procesu, którego należy to `ICorDebugThread` część stanowi.|  
|[GetRegisterSet, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Pobiera wskaźnik interfejsu do zestawu rejestru skojarzonych z tym `ICorDebugThread`.|  
|[GetUserState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Pobiera bitowa kombinacja wartości cordebuguserstate —, które opisują bieżący stan to `ICorDebugThread`.|  
|[SetDebugState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Bitowa kombinacja ustawia `CorDebugThreadState` wartości, które opisują stan debugowania `ICorDebugThread`.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
