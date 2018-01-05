---
title: Wyliczenie CorDebugDebugEventKind
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDebugEventKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90cd2b8d02cb1d16e4932ffdcc3c9b02dc71541a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugdebugeventkind-enumeration"></a>Wyliczenie CorDebugDebugEventKind
Wskazuje typ zdarzenia, których dane są dekodowane przez [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|Zdarzenie ładowania typu modułu.|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|To zdarzenie zwalnianie modułu.|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|Wyjątkach pierwszej szansy.|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|Wyjątek pierwszej szansy użytkownika.|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|Wystąpił wyjątek, dla którego `catch` Obsługa istnieje.|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|Wystąpił nieobsługiwany wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 Członek `CorDebugDebugEventKind` wyliczenie jest zwracany przez wywołanie metody [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.  
  
> [!NOTE]
>  To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
