---
title: Interfejs ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f838c9c2775023583b6879ea4c4a52727065114
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911264"
---
# <a name="icordebugdebugevent-interface"></a>Interfejs ICorDebugDebugEvent
Definiuje interfejs podstawowy, z którego pochodzą `ICorDebug` wszystkie zdarzenia debugowania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetEventKind, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|Wskazuje, jaki rodzaj zdarzenia reprezentuje `ICorDebugDebugEvent` ten obiekt.|  
|[GetThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|Pobiera wątek, w którym wystąpiło zdarzenie.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące interfejsy pochodzą od `ICorDebugDebugEvent` interfejsu:  
  
- [ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [ICorDebugModuleDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> Interfejs jest dostępny tylko z .NET Native. Próba wywołania metody `QueryInterface` pobierającej wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
