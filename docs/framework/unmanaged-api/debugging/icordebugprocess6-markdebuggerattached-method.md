---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: c83d6e892b89e6e50779abf9a71a2cbe9093af2c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212854"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>Metoda ICorDebugProcess6::MarkDebuggerAttached
Zmienia wewnętrzny stan debugee, tak aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> Metoda w bibliotece klas .NET Framework zwracana `true` .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fIsAttached`  
 `true`Jeśli <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> Metoda powinna wskazywać, że debuger jest dołączony; `false` w przeciwnym razie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda może zwracać wartości wymienione w poniższej tabeli.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|`S_OK`|Pomyślnie Zaktualizowano debugowanego obiektu.|  
|`CORDBG_E_MODULE_NOT_LOADED`|Zestaw, który zawiera <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metodę, nie został załadowany lub jakiś inny błąd, taki jak brakujące metadane, uniemożliwia jego rozpoznanie.<br /><br /> Ten błąd jest typowy i niegroźny. Należy wywołać metodę ponownie, gdy dodatkowe zestawy są ładowane.|  
|Inne błędne `HRESULT` wartości.|Inne wartości najkorzystnie wskazują debuger błędna lub składniki kompilatora.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejs ICorDebugProcess6](icordebugprocess6-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
