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
ms.openlocfilehash: e7de3622498e8417a961e0d4708c53527a833ef2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Icordebugprocess8 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
