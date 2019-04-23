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
ms.openlocfilehash: 3387985ebf6027b9cd9dee372190da65939dbae3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098627"
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
