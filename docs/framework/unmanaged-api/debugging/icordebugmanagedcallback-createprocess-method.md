---
title: ICorDebugManagedCallback::CreateProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
ms.openlocfilehash: d773368c85fd42fd169109cf1c7e6635705ebb7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090229"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a>ICorDebugManagedCallback::CreateProcess — Metoda
Powiadamia debuger, gdy proces został dołączony lub uruchomiony po raz pierwszy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 podczas Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który został dołączony lub uruchomiony.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest wywoływana do momentu zainicjowania środowiska uruchomieniowego języka wspólnego. Większość metod [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) zwróci CORDBG_E_NOTREADY przed wywołaniem zwrotnym `CreateProcess`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
