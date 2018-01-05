---
title: ICorDebugThread Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread
helpviewer_keywords: ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2df43a35e510695d7af0c38cbb8fb3b051f5f354
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread-interface1"></a>ICorDebugThread Interface1
Reprezentuje wątek w procesie. Okres istnienia `ICorDebugThread` wystąpienie jest taki sam jak okres istnienia reprezentuje wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearCurrentException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Ta metoda nie jest zaimplementowana. Nie używaj go.|  
|[CreateEval, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Tworzy obiekt ICorDebugEval, który działa na tym `ICorDebugThread`.|  
|[CreateStepper, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Tworzy obiekt ICorDebugStepper —, który umożliwia krokowe aktywną ramkę w tym `ICorDebugThread`.|  
|[EnumerateChains, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Pobiera wskaźnika interfejsu, aby moduł wyliczający ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu w tym `ICorDebugThread`.|  
|[GetActiveChain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Pobiera wskaźnika interfejsu do aktywnego ICorDebugChain na tym `ICorDebugThread`.|  
|[GetActiveFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Pobiera wskaźnika interfejsu do aktywnego ICorDebugFrame na tym `ICorDebugThread`.|  
|[GetAppDomain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Pobiera wskaźnika interfejsu do domeny aplikacji, w której ta `ICorDebugThread` jest aktualnie wykonywany.|  
|[GetCurrentException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Pobiera wskaźnika interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek obecnie wywoływany przez kod zarządzany.|  
|[GetDebugState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Pobiera wartość CorDebugThreadState, które opisują bieżący stan debugowania to `ICorDebugThread`.|  
|[GetHandle, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Pobiera bieżący dojścia dla części active `ICorDebugThread`.|  
|[GetID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Pobiera identyfikator bieżącego systemu operacyjnego części active `ICorDebugThread`.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Pobiera wskaźnika interfejsu do wspólnego języka wątku środowiska uruchomieniowego (języka wspólnego CLR).|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Pobiera wskaźnika interfejsu, na którym znajduje się ten proces `ICorDebugThread` część stanowi.|  
|[GetRegisterSet, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Pobiera wskaźnika interfejsu do zestawu rejestru, skojarzone z tym `ICorDebugThread`.|  
|[GetUserState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Pobiera bitowe połączenie wartości CorDebugUserState, które opisują bieżący stan to `ICorDebugThread`.|  
|[SetDebugState, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Ustawia bitowe połączenie `CorDebugThreadState` wartości, które opisują stan debugowania `ICorDebugThread`.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
