---
title: Interfejs ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a2543a9629c60fde2b2f14c11898ba3e9df3c82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419315"
---
# <a name="icordebugdebugevent-interface"></a>Interfejs ICorDebugDebugEvent
Definiuje interfejs podstawowy, z którym wszystkie `ICorDebug` pochodzi zdarzeń debugowania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetEventKind, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|To wskazuje jakiego rodzaju zdarzenia `ICorDebugDebugEvent` reprezentuje obiekt.|  
|[GetThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|Pobiera wątku, w którym wystąpiło zdarzenie.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące interfejsy są uzyskiwane z `ICorDebugDebugEvent` interfejsu:  
  
-   [ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [ICorDebugModuleDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  Interfejs jest tylko dostępne z platformą .NET Native. Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
