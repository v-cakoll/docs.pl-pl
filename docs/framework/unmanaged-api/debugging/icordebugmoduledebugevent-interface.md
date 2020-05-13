---
title: ICorDebugModuleDebugEvent, interfejs
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: ec6bad730d807b9a36ce5bba1c6f5d80da375f6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213336"
---
# <a name="icordebugmoduledebugevent-interface"></a>ICorDebugModuleDebugEvent, interfejs
Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) w celu obsługi zdarzeń na poziomie modułu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetModule — Metoda](icordebugmoduledebugevent-getmodule-method.md)|Pobiera scalony moduł, który został właśnie załadowany lub zwolniony.|  
  
## <a name="remarks"></a>Uwagi  
 Typy zdarzeń [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) i [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) implementują ten interfejs.  
  
> [!NOTE]
> Interfejs jest dostępny tylko z .NET Native. Próba wywołania metody `QueryInterface` pobierającej wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
