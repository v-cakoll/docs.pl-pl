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
ms.openlocfilehash: 4306c4ae44b0ae1ade2bf374981492fa1a4df76f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788368"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage — Metoda
Powiadamia debuger, że wątek zarządzany środowiska uruchomieniowego języka wspólnego (CLR) wezwał metodę w klasie <xref:System.Diagnostics.EventLog>, aby zarejestrować zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą zarządzany wątek, który zarejestrował zdarzenie.  
  
 `pThread`  
 podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek zarządzany.  
  
 `lLevel`  
 podczas Wartość wyliczenia [LoggingLevelEnum —](logginglevelenum-enumeration.md) , która wskazuje poziom ważności komunikatu opisowego, który został zapisany w dzienniku zdarzeń.  
  
 `pLogSwitchName`  
 podczas Wskaźnik do nazwy przełącznika śledzenia.  
  
 `pMessage`  
 podczas Wskaźnik do wiadomości, która została zapisywana w dzienniku zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)
