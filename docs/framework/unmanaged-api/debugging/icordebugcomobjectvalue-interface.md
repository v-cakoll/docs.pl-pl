---
title: ICorDebugComObjectValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4db005e1de043e60ffe958de732a5280fcccbea7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529950"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue — Interfejs
Udostępnia metody, aby pobrać informacje skojarzone z wywoływana otoka środowiska uruchomieniowego (RCW).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCachedInterfacePointers, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Pobiera wskaźniki interfejsu raw, buforowane na bieżącym RCW.|  
|[GetCachedInterfaceTypes, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Dostarcza moduł wyliczający dla typów interfejsu, czy bieżący obiekt został z uwzględnieniem wielkości liter do lub używany jako.|  
  
## <a name="remarks"></a>Uwagi  
 Aby sprawdzić, czy wystąpienie interfejsu "ICorDebugValue" reprezentuje RCW, wywołuje debugera `QueryInterface` na "ICorDebugValue" za pomocą `IID_ICorDebugComObjectValue`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
