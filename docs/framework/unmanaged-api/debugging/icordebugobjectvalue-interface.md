---
title: ICorDebugObjectValue — Interfejs
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
ms.openlocfilehash: b782207503a2c3f739a30f68d509e6b481d2b6a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129752"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue — Interfejs

Podklasa elementu "ICorDebugValue" reprezentująca wartość, która zawiera obiekt.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Pobiera wskaźnik interfejsu do <xref:System.Type> środowiska uruchomieniowego języka wspólnego (CLR) obiektu, do którego odwołuje się ta `ICorDebugObjectValue`.|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Nie zaimplementowane.|  
|[GetFieldValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Pobiera wskaźnik interfejsu do elementu [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , który reprezentuje wartość określonego pola określonej klasy.|  
|[GetManagedCopy, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Nieaktualne. Nie wywołuj tej metody.|  
|[GetVirtualMethod, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Nie zaimplementowane.|  
|[IsValueClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Pobiera wartość wskazującą, czy obiekt, do którego odwołuje się ten `ICorDebugObjectValue`, jest typem wartości.|  
|[SetFromManagedCopy, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Nieaktualne. Nie wywołuj tej metody.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugObjectValue` pozostaje ważna do momentu kontynuowania debugowanego procesu.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
