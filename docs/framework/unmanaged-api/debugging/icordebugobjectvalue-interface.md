---
title: ICorDebugObjectValue, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ca59aac075a42294026ad54c5d5dd4dbf7fda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943334"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue, interfejs

Podklasa elementu "ICorDebugValue" reprezentująca wartość, która zawiera obiekt.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Pobiera wskaźnik interfejsu do środowiska uruchomieniowego języka wspólnego (CLR) <xref:System.Type> obiektu, do którego odwołuje się to `ICorDebugObjectValue` odwołanie.|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Nie zaimplementowane.|  
|[GetFieldValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Pobiera wskaźnik interfejsu do elementu [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , który reprezentuje wartość określonego pola określonej klasy.|  
|[GetManagedCopy, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Nieaktualne. Nie wywołuj tej metody.|  
|[GetVirtualMethod, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Nie zaimplementowane.|  
|[IsValueClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Pobiera wartość wskazującą, czy obiekt, do którego odwołuje `ICorDebugObjectValue` się to typ wartości.|  
|[SetFromManagedCopy, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Nieaktualne. Nie wywołuj tej metody.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugObjectValue` Pozostanie on ważny do momentu, gdy debugowany proces jest kontynuowany.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
