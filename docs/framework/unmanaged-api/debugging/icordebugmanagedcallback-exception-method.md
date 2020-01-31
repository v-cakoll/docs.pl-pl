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
ms.openlocfilehash: 328c10c1895f65b43dc365b1be6b4ec5ef01e720
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777360"
---
# <a name="icordebugmanagedcallbackexception-method"></a>ICorDebugManagedCallback::Exception — Metoda
Powiadamia debugera o wygenerowanym wyjątku z kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w której został zgłoszony wyjątek.  
  
 `pThread`  
 podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym został zgłoszony wyjątek.  
  
 `unhandled`  
 podczas Jeśli ta wartość jest `false`, wyjątek nie został jeszcze przetworzony przez aplikację; w przeciwnym razie wyjątek jest nieobsługiwany i zakończy proces.  
  
## <a name="remarks"></a>Uwagi  
 Konkretny wyjątek można pobrać z obiektu wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)
