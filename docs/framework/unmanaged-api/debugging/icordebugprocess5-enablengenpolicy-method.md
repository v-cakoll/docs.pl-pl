---
title: ICorDebugProcess5::EnableNGENPolicy — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 154243e45a41ec2ba8b02937794b372a0705d458
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61930367"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy — Metoda
Ustawia wartość określającą, jak aplikacja ładuje obrazy natywne podczas uruchamiania w debugerze zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ePolicy`  
 [in] A [cordebugngenpolicy —](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) stałą, która określa, jak aplikacja ładuje obrazy natywne podczas uruchamiania w debugerze zarządzanych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zasady zostały ustawione pomyślnie, metoda zwraca `S_OK`. Jeśli `ePolicy` znajduje się poza zakresem wartości wyliczane definicją [cordebugngenpolicy —](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), metoda zwraca `E_INVALIDARG` i wywołania metody które nie ma wpływu. Jeśli nie można zaktualizować zasad Native Image Generator (Ngen.exe), metoda zwraca `E_FAIL`.  
  
 `ICorDebugProcess5::EnableNGenPolicy` Metodę można wywołać w dowolnym momencie podczas okresu istnienia procesu. Zasady są włączone dla wszelkich modułów, które są ładowane po ustawieniu zasad.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
