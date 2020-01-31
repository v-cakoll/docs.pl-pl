---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: b2ecd6da11bffb156826fa0c31b5f32abb54ff4a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792218"
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
  
## <a name="return-value"></a>Wartość zwrócona  
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

- [ICorDebugProcess6, interfejs](icordebugprocess6-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
