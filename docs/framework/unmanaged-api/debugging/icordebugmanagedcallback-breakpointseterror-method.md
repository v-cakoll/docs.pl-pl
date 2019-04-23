---
title: ICorDebugManagedCallback::BreakpointSetError — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27d5b8e0127971cc3a46560590fd9d95f0ffd1f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151024"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a>ICorDebugManagedCallback::BreakpointSetError — Metoda
Powiadamia debuger środowiska uruchomieniowego języka wspólnego i nie można powiązać dokładnie punkcie przerwania, który został ustawiony, aby funkcja była just-in-time (JIT) skompilowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera niepowiązanych punktu przerwania.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który zawiera niepowiązanych punktu przerwania.  
  
 `pBreakpoint`  
 [in] Wskaźnik do obiektu ICorDebugBreakpoint, który reprezentuje niepowiązanych punktu przerwania.  
  
 `dwError`  
 [in] Liczba całkowita, która wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Dany punkt przerwania, nigdy nie zostanie uruchomiona. Debuger powinien dezaktywować i powiąż ją ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
