---
title: Interfejs ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: 4ad350e36ee15d7c1781e03698fbee3fd40c4c12
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212870"
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
|[MarkDebuggerAttached, metoda](icordebugprocess6-markdebuggerattached-method.md)|Zmienia wewnętrzny stan debugee, tak aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> Metoda w bibliotece klas .NET Framework zwracana `true` .|  
|[Metoda ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)|Powiadamia [ICorDebug](icordebug-interface.md) o tym, że proces jest uruchomiony.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Interfejs jest dostępny tylko z .NET Native. Próba wywołania metody `QueryInterface` pobierającej wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
