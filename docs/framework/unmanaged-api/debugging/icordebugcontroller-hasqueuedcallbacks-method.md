---
title: ICorDebugController::HasQueuedCallbacks — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eba265b727d00690ab77c6ae831e954d59df7c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411613"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks — Metoda
Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne aktualnie czekają w kolejce dla określonego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 [in] Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątku.  
  
 `pbQueued`  
 [out] Wskaźnik do wartości, która jest `true` Jeśli wszystkie zarządzane wywołań zwrotnych są obecnie w kolejce dla określonego wątku; w przeciwnym razie `false`.  
  
 Jeśli określono wartość null dla `pThread` parametru `HasQueuedCallbacks` zwróci `true` Jeśli obecnie zarządzane wywołania zwrotne w kolejce na którymkolwiek wątku.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania zwrotne zostaną wysłane pojedynczo, zawsze [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) jest wywoływana. Debuger można sprawdzić tej flagi, jeśli chce, aby zgłosić wiele zdarzeń debugowania, które występowały jednocześnie.  
  
 Podczas debugowania zdarzenia są umieszczane w kolejce, ich ma już wystąpił, debuger musi opróżniania kolejki całego aby upewnić się, że stan debugowany. (Wywołania `ICorDebugController::Continue` do opróżnienia kolejki.) Na przykład, jeśli kolejka zawiera dwa zdarzenia debugowania w wątku *X*, i debuger wstrzymuje wątku *X* po pierwsze zdarzenie debugowania, a następnie wywołania `ICorDebugController::Continue`, drugie zdarzenie debugowania dla Wątek *X* zostanie wysłane, mimo że wątek został wstrzymany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
