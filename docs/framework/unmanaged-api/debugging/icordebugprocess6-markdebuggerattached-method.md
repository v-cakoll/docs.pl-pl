---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c818b196f3252138f2a9c601b04f1d7a6727bc6b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912740"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>Metoda ICorDebugProcess6::MarkDebuggerAttached
Zmienia wewnętrzny stan debugee, tak aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> Metoda w bibliotece klas .NET Framework zwracana. `true`  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fIsAttached`  
 `true`<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> Jeśli metoda powinna wskazywać, że debuger jest dołączony; `false` w przeciwnym razie.  
  
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
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess6, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
