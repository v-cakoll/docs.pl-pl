---
title: ICorDebugManagedCallback::Exception — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91318ea596cc7d6c8a747901fea2749a64aa2623
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168119"
---
# <a name="icordebugmanagedcallbackexception-method"></a>ICorDebugManagedCallback::Exception — Metoda
Powiadamia debuger zgłoszony wyjątek z kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w którym wystąpił wyjątek.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym wystąpił wyjątek.  
  
 `unhandled`  
 [in] Jeśli ta wartość jest `false`, wyjątek jeszcze nie zostały przetworzone przez aplikację; w przeciwnym razie, wyjątek nie jest obsługiwana i zakończy proces.  
  
## <a name="remarks"></a>Uwagi  
 Określony wyjątek, mogą być pobierane z obiektu wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
