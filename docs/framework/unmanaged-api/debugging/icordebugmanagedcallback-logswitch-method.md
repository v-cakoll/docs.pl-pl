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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 040c7dea7f751accb801f8fda190e9387c7aede1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466170"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch — Metoda
Informuje debuger, wspólnym mianownikiem zarządzanych środowiska uruchomieniowego (języka wspólnego CLR) języka została wywołana metoda <xref:System.Diagnostics.Switch> klasy, aby utworzyć, zmodyfikować lub usunąć przełącznik debugowanie śledzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierająca zarządzane wątku, który utworzone, zmodyfikowane lub usunięte przełącznik debugowanie śledzenia.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątków zarządzanych.  
  
 `lLevel`  
 [in] Wartość, która wskazuje poziom ważności opisowy komunikat, który został zapisany w dzienniku zdarzeń.  
  
 `ulReason`  
 [in] Wartość [logswitchcallreason —](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) wyliczenie, które wskazuje operację wykonywane na przełączniku debugowanie śledzenia.  
  
 `pLogSwitchName`  
 [in] Wskaźnik na nazwę przełącznika debugowanie śledzenia.  
  
 `pParentName`  
 [in] Wskaźnik na nazwę elementu nadrzędnego przełącznik debugowanie śledzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
