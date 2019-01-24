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
ms.openlocfilehash: 7ae0838dd5f4dcfe95cd516b23fef3d5ca429031
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586376"
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
  
#### <a name="parameters"></a>Parametry  
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
