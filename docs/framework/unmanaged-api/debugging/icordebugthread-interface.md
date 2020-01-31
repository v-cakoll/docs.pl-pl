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
ms.openlocfilehash: b227b374021136e78f7f061d235eb18eca5b9515
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791474"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread, interfejs
Reprezentuje wątek w procesie. Okres istnienia wystąpienia `ICorDebugThread` jest taki sam jak okres istnienia wątku, który reprezentuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearCurrentException, metoda](icordebugthread-clearcurrentexception-method.md)|Ta metoda nie jest zaimplementowana. Nie używaj go.|  
|[CreateEval, metoda](icordebugthread-createeval-method.md)|Tworzy obiekt ICorDebugEval, który działa na tym `ICorDebugThread`.|  
|[CreateStepper, metoda](icordebugthread-createstepper-method.md)|Tworzy obiekt ICorDebugStepper, który umożliwia przechodzenie przez aktywną ramkę w tym `ICorDebugThread`.|  
|[EnumerateChains, metoda](icordebugthread-enumeratechains-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu w tym `ICorDebugThread`.|  
|[GetActiveChain, metoda](icordebugthread-getactivechain-method.md)|Pobiera wskaźnik interfejsu do aktywnego ICorDebugChain na tym `ICorDebugThread`.|  
|[GetActiveFrame, metoda](icordebugthread-getactiveframe-method.md)|Pobiera wskaźnik interfejsu do aktywnego ICorDebugFrame na tym `ICorDebugThread`.|  
|[GetAppDomain, metoda](icordebugthread-getappdomain-method.md)|Pobiera wskaźnik interfejsu do domeny aplikacji, w której jest aktualnie wykonywany ten `ICorDebugThread`.|  
|[GetCurrentException, metoda](icordebugthread-getcurrentexception-method.md)|Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek, który jest aktualnie generowany przez kod zarządzany.|  
|[GetDebugState, metoda](icordebugthread-getdebugstate-method.md)|Pobiera wartość CorDebugThreadState —, która opisuje bieżący stan debugowania tego `ICorDebugThread`.|  
|[GetHandle, metoda](icordebugthread-gethandle-method.md)|Pobiera bieżące dojście dla aktywnej części tego `ICorDebugThread`.|  
|[GetID, metoda](icordebugthread-getid-method.md)|Pobiera bieżący identyfikator systemu operacyjnego aktywnej części tego `ICorDebugThread`.|  
|[GetObject, metoda](icordebugthread-getobject-method.md)|Pobiera wskaźnik interfejsu do wątku środowiska uruchomieniowego języka wspólnego (CLR).|  
|[GetProcess, metoda](icordebugthread-getprocess-method.md)|Pobiera wskaźnik interfejsu do procesu, którego `ICorDebugThread` stanowi część.|  
|[GetRegisterSet, metoda](icordebugthread-getregisterset-method.md)|Pobiera wskaźnik interfejsu do zestawu rejestru skojarzonego z tym `ICorDebugThread`.|  
|[GetUserState, metoda](icordebugthread-getuserstate-method.md)|Pobiera bitową kombinację wartości CorDebugUserState —, które opisują bieżący stan tego `ICorDebugThread`.|  
|[SetDebugState, metoda](icordebugthread-setdebugstate-method.md)|Ustawia bitową kombinację wartości `CorDebugThreadState`, które opisują stan debugowania tego `ICorDebugThread`.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
