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
ms.openlocfilehash: 583819e8e7ab16a8ac1ce72892f4353e3043ce3d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129688"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy — Metoda
Ustawia wartość określającą sposób ładowania obrazów natywnych przez aplikację podczas działania w ramach zarządzanego debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ePolicy`  
 podczas Stała [CorDebugNGenPolicy —](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) , która określa, w jaki sposób aplikacja ładuje obrazy natywne podczas działania w zarządzanym debugerze.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zasady zostały ustawione pomyślnie, metoda zwraca `S_OK`. Jeśli `ePolicy` znajduje się poza zakresem wartości wyliczanych zdefiniowanych przez [CorDebugNGenPolicy —](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), metoda zwraca `E_INVALIDARG` i wywołanie metody nie ma żadnego wpływu. Jeśli nie można zaktualizować zasad generatora obrazów natywnych (Ngen. exe), metoda zwraca `E_FAIL`.  
  
 Metodę `ICorDebugProcess5::EnableNGenPolicy` można wywołać w dowolnym momencie w okresie istnienia procesu. Zasady obowiązują dla wszystkich modułów, które są ładowane po ustawieniu zasad.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
