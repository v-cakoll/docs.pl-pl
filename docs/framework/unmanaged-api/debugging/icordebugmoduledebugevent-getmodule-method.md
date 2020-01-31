---
title: 'ICorDebugModuleDebugEvent:: GetModule — Metoda'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 4d9eea8fb5c42002763a0ae52a186bf2c1e6d2ee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792910"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a>ICorDebugModuleDebugEvent:: GetModule — Metoda
Pobiera scalony moduł, który został właśnie załadowany lub zwolniony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppModule`  
 określoną Wskaźnik do adresu obiektu ICorDebugModule, który reprezentuje scalony moduł, który został właśnie załadowany lub zwolniony.  
  
## <a name="remarks"></a>Uwagi  
 Można wywołać metodę [GetEventKind](icordebugdebugevent-geteventkind-method.md) , aby określić, czy moduł został załadowany, czy zwolniony.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugModuleDebugEvent, interfejs](icordebugmoduledebugevent-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
