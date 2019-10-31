---
title: ICorDebugManagedCallback::LogSwitch — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
ms.openlocfilehash: a72eabb1b405c67f5603164e56a589a237603d2f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130695"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch — Metoda
Powiadamia debuger, że wątek zarządzany środowiska uruchomieniowego języka wspólnego (CLR) wezwał metodę w klasie <xref:System.Diagnostics.Switch>, aby utworzyć, zmodyfikować lub usunąć przełącznik debugowania/śledzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a>Parametry  
 `PAppDomain`  
 podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą zarządzany wątek, który utworzył, zmodyfikował lub usunął przełącznik debugowania/śledzenia.  
  
 `pThread`  
 podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek zarządzany.  
  
 `lLevel`  
 podczas Wartość wskazująca poziom ważności komunikatu opisowego, który został zapisany w dzienniku zdarzeń.  
  
 `ulReason`  
 podczas Wartość wyliczenia [LogSwitchCallReason —](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) , która wskazuje operację wykonywaną na przełączniku debugowania/śledzenia.  
  
 `pLogSwitchName`  
 podczas Wskaźnik do nazwy przełącznika debugowania/śledzenia.  
  
 `pParentName`  
 podczas Wskaźnik do nazwy elementu nadrzędnego przełącznika debugowania/śledzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
