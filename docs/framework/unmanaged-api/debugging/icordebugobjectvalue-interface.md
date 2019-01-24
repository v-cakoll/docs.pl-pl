---
title: ICorDebugObjectValue Interface1
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
ms.openlocfilehash: 5cd991049c159b96a0f0717b31d6a2834b250f70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631996"
---
# <a name="icordebugobjectvalue-interface1"></a>ICorDebugObjectValue Interface1
Podklasa klasy "ICorDebugValue", która reprezentuje wartość, która zawiera obiekt.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Pobiera wskaźnik interfejsu do środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.Type> obiektu że `ICorDebugObjectValue` odwołania.|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Nie zaimplementowano.|  
|[GetFieldValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Pobiera wskaźnik interfejsu do [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) reprezentująca wartość określonego pola określonej klasy.|  
|[GetManagedCopy, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Nieaktualne. Nie wywołuj tej metody.|  
|[GetVirtualMethod, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Nie zaimplementowano.|  
|[IsValueClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Pobiera wartość wskazującą, czy obiekt odwołuje się ten `ICorDebugObjectValue` jest typem wartości.|  
|[SetFromManagedCopy, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Nieaktualne. Nie wywołuj tej metody.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugObjectValue` Pozostaje ważny, dopóki debugowany proces jest kontynuowany.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

