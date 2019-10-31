---
title: ICorDebugReferenceValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 16d7b89ee441e8d634c36fb87185b3f2846860b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137706"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue — Interfejs
Dostarcza metody, które zarządzają wartością, która jest odwołaniem do obiektu. (Oznacza to, że ten interfejs zapewnia metody, które zarządzają wskaźnikiem). Ten interfejs implementuje "ICorDebugValue".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dereference, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Pobiera obiekt, do którego istnieje odwołanie.|  
|[DereferenceStrong, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Nie zaimplementowane. Nie wywołuj tej metody.|  
|[GetValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Pobiera bieżący adres pamięci obiektu, do którego istnieje odwołanie.|  
|[IsNull, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Pobiera wartość wskazującą, czy ta `ICorDebugReferenceValue` jest wartością null, w której przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.|  
|[SetValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Ustawia bieżący adres pamięci. Oznacza to, że ta metoda ustawia tę `ICorDebugReferenceValue` tak, aby wskazywała na obiekt.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) może wykonywać odzyskiwanie pamięci na obiektach, gdy debugowany proces jest kontynuowany. Wyrzucanie elementów bezużytecznych może przenosić obiekty w pamięci. `ICorDebugReferenceValue` będzie współpracować z wyrzucaniem elementów bezużytecznych, dzięki czemu informacje są aktualizowane po wyrzucaniu elementów bezużytecznych lub zostaną unieważnione niejawnie przed wyrzucaniem elementów bezużytecznych.  
  
 Obiekt `ICorDebugReferenceValue` może być niejawnie unieważniony po dalszym debugowanym procesie. Pochodny element "ICorDebugHandleValue" nie jest unieważniony, dopóki nie zostanie jawnie wystawiony lub ujawniony.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
