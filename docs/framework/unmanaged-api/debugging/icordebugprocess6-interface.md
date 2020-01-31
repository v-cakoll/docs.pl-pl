---
title: Interfejs ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: 73ef1a64deaf5420246fc1ab3e9f88ba5bf049a5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792232"
---
# <a name="icordebugprocess6-interface"></a>Interfejs ICorDebugProcess6
Logicznie rozszerza interfejs ICorDebugProcess w celu włączenia takich funkcji, jak dekodowanie zdarzeń debugowania zarządzanego, które są kodowane w natywnych zdarzeniach debugowania wyjątków i dzielenia modułu wirtualnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DecodeEvent, metoda](icordebugprocess6-decodeevent-method.md)|Dekoduje zarządzane zdarzenia debugowania, które zostały hermetyzowane w ładunku specjalnie spreparowanych zdarzeń debugowania wyjątku natywnego.|  
|[EnableVirtualModuleSplitting, metoda](icordebugprocess6-enablevirtualmodulesplitting-method.md)|Włącza lub wyłącza dzielenie modułu wirtualnego.|  
|[GetCode, metoda](icordebugprocess6-getcode-method.md)|Pobiera informacje o zarządzanym kodzie pod określonym adresem kodu.|  
|[GetExportStepInfo, metoda](icordebugprocess6-getexportstepinfo-method.md)|Zawiera informacje dotyczące funkcji wyeksportowanych przez środowisko uruchomieniowe, które ułatwiają przechodzenie przez kod zarządzany.|  
|[MarkDebuggerAttached, metoda](icordebugprocess6-markdebuggerattached-method.md)|Zmienia wewnętrzny stan debugee, tak aby Metoda <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> w .NET Frameworkej bibliotece klas zwracała `true`.|  
|[ProcessStateChanged, metoda](icordebugprocess6-processstatechanged-method.md)|Powiadamia [ICorDebug](icordebug-interface.md) o tym, że proces jest uruchomiony.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Interfejs jest dostępny tylko z .NET Native. Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
