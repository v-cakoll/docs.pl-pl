---
title: "ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f13236c865f9a57d77ebf83ab48e010f06ef08e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda
[Obsługiwane w [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] i nowszych wersjach]  
  
 Włącza lub wyłącza niektórych typów [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) wyjątek wywołań zwrotnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `enableExceptionsOutsideOfJMC` jest `false`:  
  
-   Wyjątek DEBUG_EXCEPTION_FIRST_CHANCE nie spowoduje wywołanie zwrotne do debugera.  
  
-   Wyjątek DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nie spowoduje wywołanie zwrotne do debugera Jeśli wyjątek nigdy nie specjalne do kodu użytkownika (oznacza to, że ścieżka pochodzenia wyjątek do obsługi wyjątków ma żadna metoda oznaczona jako JustMyCode lub JMC).  
  
 Wartość domyślna `enableExceptionsOutsideOfJMC` jest `true`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugProcess8, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
