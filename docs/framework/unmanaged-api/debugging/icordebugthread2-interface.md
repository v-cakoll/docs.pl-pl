---
title: ICorDebugThread2 Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c348cf28a6330523d1a490c136a3214e37d13f4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423052"
---
# <a name="icordebugthread2-interface1"></a>ICorDebugThread2 Interface1
Służy jako logiczne rozszerzenia interfejsu ICorDebugThread.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetActiveFunctions, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Pobiera tablicę cor_active_function — wystąpień, które zawierają dane dotyczące funkcji active w ramkach wątku.|  
|[GetConnectionID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Pobiera identyfikator połączenia dla tego `ICorDebugThread2`.|  
|[GetTaskID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Pobiera identyfikator zadania dla tego `ICorDebugThread2`.|  
|[GetVolatileOSThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Pobiera identyfikator wątku systemu operacyjnego dla tego `ICorDebugThread2`.|  
|[InterceptCurrentException, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Umożliwia debugera przechwycić bieżącego wyjątku w wątku.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
