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
ms.openlocfilehash: 11afee9c2a84999ccad2cdc12e2a14a4dc17d542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412526"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue — Interfejs
Udostępnia metody, aby pobrać informacje związane z wywoływana otoka środowiska uruchomieniowego (otoki RCW).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCachedInterfacePointers, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Pobiera wskaźniki interfejsu pierwotnego w bieżącym otoki RCW pamięci podręcznej.|  
|[GetCachedInterfaceTypes, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Udostępnia moduł wyliczający dla typów interfejsu, czy bieżący obiekt został do wielkości liter lub używane jako.|  
  
## <a name="remarks"></a>Uwagi  
 Aby sprawdzić, czy wystąpienie interfejsu "ICorDebugValue" reprezentuje otoki RCW, wywołuje debugera `QueryInterface` na "ICorDebugValue" z `IID_ICorDebugComObjectValue`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
