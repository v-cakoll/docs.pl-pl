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
ms.openlocfilehash: e104f8c522af2ee4cd42332b7459f4a2fd185511
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792688"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue, interfejs

Podklasa elementu "ICorDebugValue" reprezentująca wartość, która zawiera obiekt.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetClass, metoda](icordebugobjectvalue-getclass-method.md)|Pobiera wskaźnik interfejsu do <xref:System.Type> środowiska uruchomieniowego języka wspólnego (CLR) obiektu, do którego odwołuje się ta `ICorDebugObjectValue`.|  
|[GetContext, metoda](icordebugobjectvalue-getcontext-method.md)|Nie zaimplementowane.|  
|[GetFieldValue, metoda](icordebugobjectvalue-getfieldvalue-method.md)|Pobiera wskaźnik interfejsu do elementu [ICorDebugValue](icordebugvalue-interface.md) , który reprezentuje wartość określonego pola określonej klasy.|  
|[GetManagedCopy, metoda](icordebugobjectvalue-getmanagedcopy-method.md)|{1&gt;Nieaktualne.&lt;1} Nie wywołuj tej metody.|  
|[GetVirtualMethod, metoda](icordebugobjectvalue-getvirtualmethod-method.md)|Nie zaimplementowane.|  
|[IsValueClass, metoda](icordebugobjectvalue-isvalueclass-method.md)|Pobiera wartość wskazującą, czy obiekt, do którego odwołuje się ten `ICorDebugObjectValue`, jest typem wartości.|  
|[SetFromManagedCopy, metoda](icordebugobjectvalue-setfrommanagedcopy-method.md)|{1&gt;Nieaktualne.&lt;1} Nie wywołuj tej metody.|  
  
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

- [Debugowanie, interfejsy](debugging-interfaces.md)
