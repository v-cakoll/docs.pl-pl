---
title: Interfejs ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518c6ec99e4062bf8432809d3472baa395017da3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147267"
---
# <a name="icordebugprocess6-interface"></a>Interfejs ICorDebugProcess6
Rozszerza logicznie icordebugprocess — interfejs, aby włączyć funkcje, takie jak dekodowanie zdarzenia debugowania zarządzanego, które są kodowane w zdarzeń debugowania natywnych wyjątków oraz wirtualnego modułu dzielenia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DecodeEvent, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|Dekoduje zdarzenia debugowania zarządzanego, które zostały hermetyzowane w ładunku zdarzenia debugowania specjalnie przygotowane natywnych wyjątek.|  
|[EnableVirtualModuleSplitting, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|Włącza lub wyłącza wirtualnego modułu dzielenia.|  
|[GetCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|Pobiera informacje o kodzie zarządzanym pod adresem określonym kodem.|  
|[GetExportStepInfo, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|Zawiera informacje na temat funkcji środowiska uruchomieniowego wyeksportowane ułatwiające Przechodź przez kod zarządzany.|  
|[MarkDebuggerAttached, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|Zmienia stan wewnętrzny debugee tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> zwraca metody w bibliotece klas programu .NET Framework `true`.|  
|[ProcessStateChanged, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , proces jest uruchomiony.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Interfejs jest tylko dostępne z architekturą .NET Native. Próba wywołania `QueryInterface` do pobrania wskaźnika interfejsu zwraca `E_NOINTERFACE` scenariuszach ICorDebug poza .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
