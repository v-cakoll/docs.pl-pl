---
title: Interfejs ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: ac26402903ecf437fa9654e91cef8b44ff033358
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123448"
---
# <a name="icordebugprocess6-interface"></a>Interfejs ICorDebugProcess6
Logicznie rozszerza interfejs ICorDebugProcess w celu włączenia takich funkcji, jak dekodowanie zdarzeń debugowania zarządzanego, które są kodowane w natywnych zdarzeniach debugowania wyjątków i dzielenia modułu wirtualnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DecodeEvent, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|Dekoduje zarządzane zdarzenia debugowania, które zostały hermetyzowane w ładunku specjalnie spreparowanych zdarzeń debugowania wyjątku natywnego.|  
|[EnableVirtualModuleSplitting, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|Włącza lub wyłącza dzielenie modułu wirtualnego.|  
|[GetCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|Pobiera informacje o zarządzanym kodzie pod określonym adresem kodu.|  
|[GetExportStepInfo, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|Zawiera informacje dotyczące funkcji wyeksportowanych przez środowisko uruchomieniowe, które ułatwiają przechodzenie przez kod zarządzany.|  
|[MarkDebuggerAttached, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|Zmienia wewnętrzny stan debugee, tak aby Metoda <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> w .NET Frameworkej bibliotece klas zwracała `true`.|  
|[ProcessStateChanged, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|Powiadamia [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) o tym, że proces jest uruchomiony.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Interfejs jest dostępny tylko z .NET Native. Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
