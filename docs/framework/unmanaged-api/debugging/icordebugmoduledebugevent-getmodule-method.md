---
title: Metoda ICorDebugModuleDebugEvent::GetModule
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c0cc1305f47f03c8c9b35bab5c980cb23d1b157
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138440"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a>Metoda ICorDebugModuleDebugEvent::GetModule
Pobiera scalonych moduł, który został właśnie załadowany lub usunięty z pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppModule`  
 [out] Wskaźnik na adres ICorDebugModule obiekt, który reprezentuje scalonych moduł, który właśnie został załadowany lub zwolnione.  
  
## <a name="remarks"></a>Uwagi  
 Możesz wywołać [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metodę, aby ustalić, czy moduł został załadowany lub zwolnione.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugModuleDebugEvent, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
