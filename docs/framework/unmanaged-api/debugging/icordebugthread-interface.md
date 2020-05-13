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
ms.openlocfilehash: edcc0ebcadc1bd95574b0276bfd0e2d42e5474fd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379817"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread, interfejs
Reprezentuje wątek w procesie. Okres istnienia `ICorDebugThread` wystąpienia jest taki sam jak okres istnienia wątku, który reprezentuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearCurrentException, metoda](icordebugthread-clearcurrentexception-method.md)|Ta metoda nie jest zaimplementowana. Nie używaj go.|  
|[CreateEval, metoda](icordebugthread-createeval-method.md)|Tworzy obiekt ICorDebugEval, który działa na tym `ICorDebugThread` .|  
|[CreateStepper — Metoda](icordebugthread-createstepper-method.md)|Tworzy obiekt ICorDebugStepper, który umożliwia przechodzenie przez aktywną ramkę w tym elemencie `ICorDebugThread` .|  
|[EnumerateChains, metoda](icordebugthread-enumeratechains-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu w tym elemencie `ICorDebugThread` .|  
|[GetActiveChain, metoda](icordebugthread-getactivechain-method.md)|Pobiera wskaźnik interfejsu do aktywnego ICorDebugChain `ICorDebugThread` .|  
|[GetActiveFrame — Metoda](icordebugthread-getactiveframe-method.md)|Pobiera wskaźnik interfejsu do aktywnego ICorDebugFrame `ICorDebugThread` .|  
|[GetAppDomain, metoda](icordebugthread-getappdomain-method.md)|Pobiera wskaźnik interfejsu do domeny aplikacji, w której `ICorDebugThread` jest aktualnie wykonywany.|  
|[GetCurrentException, metoda](icordebugthread-getcurrentexception-method.md)|Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek, który jest aktualnie generowany przez kod zarządzany.|  
|[GetDebugState, metoda](icordebugthread-getdebugstate-method.md)|Pobiera wartość CorDebugThreadState —, która opisuje bieżący stan debugowania tego elementu `ICorDebugThread` .|  
|[GetHandle, metoda](icordebugthread-gethandle-method.md)|Pobiera bieżące dojście dla aktywnej części tego elementu `ICorDebugThread` .|  
|[GetID, metoda](icordebugthread-getid-method.md)|Pobiera bieżący identyfikator systemu operacyjnego aktywnej części tego elementu `ICorDebugThread` .|  
|[GetObject — Metoda](icordebugthread-getobject-method.md)|Pobiera wskaźnik interfejsu do wątku środowiska uruchomieniowego języka wspólnego (CLR).|  
|[GetProcess — Metoda](icordebugthread-getprocess-method.md)|Pobiera wskaźnik interfejsu do procesu, którego `ICorDebugThread` częścią jest ten element.|  
|[GetRegisterSet — Metoda](icordebugthread-getregisterset-method.md)|Pobiera wskaźnik interfejsu do zestawu rejestru skojarzonego z tym elementem `ICorDebugThread` .|  
|[GetUserState, metoda](icordebugthread-getuserstate-method.md)|Pobiera bitową kombinację wartości CorDebugUserState —, które opisują bieżący stan tego elementu `ICorDebugThread` .|  
|[SetDebugState, metoda](icordebugthread-setdebugstate-method.md)|Ustawia bitową kombinację `CorDebugThreadState` wartości opisujących stan debugowania tego elementu `ICorDebugThread` .|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
