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
ms.workload: dotnet
ms.openlocfilehash: 9928018b7d4065fbf24b4c39f7ef2d121e66d7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6-interface"></a>Interfejs ICorDebugProcess6
Logicznie rozszerza interfejs ICorDebugProcess, aby włączyć funkcje, takie jak dekodowania zdarzenia debugowania zarządzanego, które są zakodowane w zdarzenia debugowania natywnego wyjątków i dzielenia wirtualnych modułu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DecodeEvent, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|Dekoduje zdarzenia debugowania zarządzanego, które zostały hermetyzowany w ładunku zdarzenia debugowania specjalnie przygotowany natywnego wyjątków.|  
|[EnableVirtualModuleSplitting, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|Włącza lub wyłącza wirtualnego modułu dzielenia.|  
|[GetCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|Pobiera informacje o zarządzanego kodu pod adresem określonym kodem.|  
|[GetExportStepInfo, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|Zawiera informacje dotyczące środowiska uruchomieniowego wyeksportowane funkcje ułatwiające krok za pomocą kodu zarządzanego.|  
|[MarkDebuggerAttached, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|Wewnętrzny stan klasy obiektu debugowanego zmiany, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda w bibliotece klas programu .NET Framework zwraca `true`.|  
|[ProcessStateChanged, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) którym jest uruchomiony proces.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Interfejs jest tylko dostępne z platformą .NET Native. Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
