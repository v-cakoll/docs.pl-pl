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
ms.openlocfilehash: 38ff08fa7e7db986006c4e0e09b1ac9cf1be801e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767148"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy — Metoda
Ustawia wartość określającą, jak aplikacja ładuje obrazy natywne podczas uruchamiania w debugerze zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
