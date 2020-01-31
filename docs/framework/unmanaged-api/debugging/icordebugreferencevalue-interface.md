---
title: ICorDebugReferenceValue, interfejs
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
ms.openlocfilehash: 2efba22b4ec372c5ddedd4982a29d66945d3511c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792134"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue, interfejs
Dostarcza metody, które zarządzają wartością, która jest odwołaniem do obiektu. (Oznacza to, że ten interfejs zapewnia metody, które zarządzają wskaźnikiem). Ten interfejs implementuje "ICorDebugValue".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dereference, metoda](icordebugreferencevalue-dereference-method.md)|Pobiera obiekt, do którego istnieje odwołanie.|  
|[DereferenceStrong, metoda](icordebugreferencevalue-dereferencestrong-method.md)|Nie zaimplementowane. Nie wywołuj tej metody.|  
|[GetValue, metoda](icordebugreferencevalue-getvalue-method.md)|Pobiera bieżący adres pamięci obiektu, do którego istnieje odwołanie.|  
|[IsNull, metoda](icordebugreferencevalue-isnull-method.md)|Pobiera wartość wskazującą, czy ta `ICorDebugReferenceValue` jest wartością null, w której przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.|  
|[SetValue, metoda](icordebugreferencevalue-setvalue-method.md)|Ustawia bieżący adres pamięci. Oznacza to, że ta metoda ustawia tę `ICorDebugReferenceValue` tak, aby wskazywała na obiekt.|  
  
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

- [Debugowanie, interfejsy](debugging-interfaces.md)
