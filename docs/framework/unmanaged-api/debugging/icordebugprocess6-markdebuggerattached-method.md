---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: 48bab20a71144b28f24951556eb36210d7b6aebf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123430"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>Metoda ICorDebugProcess6::MarkDebuggerAttached
Zmienia wewnętrzny stan debugee, tak aby Metoda <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> w .NET Frameworkej bibliotece klas zwracała `true`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fIsAttached`  
 `true`, jeśli metoda <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> powinna wskazywać, że debuger jest dołączony; `false` w przeciwnym razie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda może zwracać wartości wymienione w poniższej tabeli.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|`S_OK`|Pomyślnie Zaktualizowano debugowanego obiektu.|  
|`CORDBG_E_MODULE_NOT_LOADED`|Zestaw, który zawiera metodę <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>, nie został załadowany lub jakiś inny błąd, taki jak brakujące metadane, uniemożliwia jego rozpoznanie.<br /><br /> Ten błąd jest typowy i niegroźny. Należy wywołać metodę ponownie, gdy dodatkowe zestawy są ładowane.|  
|Inne błędne wartości `HRESULT`.|Inne wartości najkorzystnie wskazują debuger błędna lub składniki kompilatora.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess6, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
