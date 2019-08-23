---
title: ICorDebugChain, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93ada40bd88e53cd06f5e8d8136b2d527d7741e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969305"
---
# <a name="icordebugchain-interface"></a>ICorDebugChain, interfejs

Reprezentuje segment stosu wywołań fizycznych lub logicznych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateFrames, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|Pobiera moduł wyliczający, który zawiera wszystkie zarządzane ramki stosu w łańcuchu, rozpoczynając od ostatniej ramki.|  
|[GetActiveFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Pobiera aktywną (czyli ostatnią) ramkę w łańcuchu.|  
|[GetCallee, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Pobiera łańcuch, który został wywołany przez ten łańcuch.|  
|[GetCaller, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Pobiera łańcuch, który wywołał ten łańcuch.|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Nie zaimplementowane.|  
|[GetNext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Pobiera następny łańcuch ramek dla wątku.|  
|[GetPrevious, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Pobiera poprzedni łańcuch ramek dla wątku.|  
|[GetReason, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Pobiera przyczynę Genesis tego łańcucha wywołującego.|  
|[GetRegisterSet, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Pobiera zestaw rejestru dla aktywnej części tego łańcucha.|  
|[GetStackRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Pobiera zakres adresów segmentu stosu dla tego łańcucha.|  
|[GetThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Pobiera wątek fizyczny, do którego należy ten łańcuch wywołań.|  
|[IsManaged, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Pobiera wartość wskazującą, czy w tym łańcuchu działa kod zarządzany.|  
  
## <a name="remarks"></a>Uwagi  
 Ramki stosu w łańcuchu zajmują ciągły obszar stosu i korzystają z tego samego wątku i kontekstu. Łańcuch może reprezentować zarządzane lub niezarządzane łańcuchy kodu. Puste `ICorDebugChain` wystąpienie reprezentuje łańcuch kodu niezarządzanego.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
