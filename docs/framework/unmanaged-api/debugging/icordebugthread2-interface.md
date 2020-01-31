---
title: ICorDebugThread2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: fdaad46b739721ff95b712d4b6461a793ae0a480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791432"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2, interfejs
Służy jako logiczne rozszerzenie interfejsu ICorDebugThread.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetActiveFunctions, metoda](icordebugthread2-getactivefunctions-method.md)|Pobiera tablicę wystąpień COR_ACTIVE_FUNCTION zawierających dane dotyczące aktywnych funkcji w ramkach wątku.|  
|[GetConnectionID, metoda](icordebugthread2-getconnectionid-method.md)|Pobiera identyfikator połączenia dla tego `ICorDebugThread2`.|  
|[GetTaskID, metoda](icordebugthread2-gettaskid-method.md)|Pobiera identyfikator zadania dla tego `ICorDebugThread2`.|  
|[GetVolatileOSThreadID, metoda](icordebugthread2-getvolatileosthreadid-method.md)|Pobiera identyfikator wątku systemu operacyjnego dla tego `ICorDebugThread2`.|  
|[InterceptCurrentException, metoda](icordebugthread2-interceptcurrentexception-method.md)|Umożliwia debugerowi przechwycenie bieżącego wyjątku w wątku.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
