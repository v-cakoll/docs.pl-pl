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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67006603747abd89f1b635c065860dcbe1c47a29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965643"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue, interfejs
Dostarcza metody, które zarządzają wartością, która jest odwołaniem do obiektu. (Oznacza to, że ten interfejs zapewnia metody, które zarządzają wskaźnikiem). Ten interfejs implementuje "ICorDebugValue".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dereference, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Pobiera obiekt, do którego istnieje odwołanie.|  
|[DereferenceStrong, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Nie zaimplementowane. Nie wywołuj tej metody.|  
|[GetValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Pobiera bieżący adres pamięci obiektu, do którego istnieje odwołanie.|  
|[IsNull, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Pobiera wartość wskazującą, czy jest to `ICorDebugReferenceValue` wartość null, w takim `ICorDebugReferenceValue` przypadku nie wskazuje na obiekt.|  
|[SetValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Ustawia bieżący adres pamięci. Oznacza to, że ta metoda ustawia `ICorDebugReferenceValue` ten element tak, aby wskazywał obiekt.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) może wykonywać odzyskiwanie pamięci na obiektach, gdy debugowany proces jest kontynuowany. Wyrzucanie elementów bezużytecznych może przenosić obiekty w pamięci. `ICorDebugReferenceValue` Program będzie współpracować z wyrzucaniem elementów bezużytecznych, aby informacje były aktualizowane po wyrzucaniu elementów bezużytecznych lub zostaną unieważnione niejawnie przed wyrzucaniem elementów bezużytecznych.  
  
 `ICorDebugReferenceValue` Obiekt może być niejawnie unieważniony po dalszym debugowanym procesie. Pochodny element "ICorDebugHandleValue" nie jest unieważniony, dopóki nie zostanie jawnie wystawiony lub ujawniony.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
