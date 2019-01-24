---
title: ICorDebugManagedCallback::LogMessage — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61a8d3e4a343818918e140727d3770ba3e82aac8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574693"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage — Metoda
Informuje debuger, wspólnym mianownikiem zarządzanych środowiska uruchomieniowego (języka wspólnego CLR) języka została wywołana metoda <xref:System.Diagnostics.EventLog> klasy, aby rejestrować zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą wątków zarządzanych, rejestrującej zdarzenie.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątków zarządzanych.  
  
 `lLevel`  
 [in] Wartość [logginglevelenum —](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) wyliczenie, które wskazuje poziom ważności opisowy komunikat, który został zapisany w dzienniku zdarzeń.  
  
 `pLogSwitchName`  
 [in] Wskaźnik na nazwę przełącznika śledzenia.  
  
 `pMessage`  
 [in] Wskaźnik do komunikat, który został zapisany w dzienniku zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
