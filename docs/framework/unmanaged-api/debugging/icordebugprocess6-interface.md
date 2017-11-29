---
title: Interfejs ICorDebugProcess6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 222007d03d8ace00f97c01cf2a02f0dc293bbf78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6-interface"></a>Interfejs ICorDebugProcess6
Logicznie rozszerza interfejs ICorDebugProcess, aby włączyć funkcje, takie jak dekodowania zdarzenia debugowania zarządzanego, które są zakodowane w zdarzenia debugowania natywnego wyjątków i dzielenia wirtualnych modułu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Metoda DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|Dekoduje zdarzenia debugowania zarządzanego, które zostały hermetyzowany w ładunku zdarzenia debugowania specjalnie przygotowany natywnego wyjątków.|  
|[Metoda EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|Włącza lub wyłącza wirtualnego modułu dzielenia.|  
|[GetCode — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|Pobiera informacje o zarządzanego kodu pod adresem określonym kodem.|  
|[Metoda GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|Zawiera informacje dotyczące środowiska uruchomieniowego wyeksportowane funkcje ułatwiające krok za pomocą kodu zarządzanego.|  
|[Metoda MarkDebuggerAttached](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|Wewnętrzny stan klasy obiektu debugowanego zmiany, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda w bibliotece klas programu .NET Framework zwraca `true`.|  
|[Metoda ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) którym jest uruchomiony proces.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Interfejs jest tylko dostępne z platformą .NET Native. Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
