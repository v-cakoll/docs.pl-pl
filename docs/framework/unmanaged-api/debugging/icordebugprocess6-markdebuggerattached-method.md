---
title: Metoda ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15e2e94ac4e30fbdb375175148a5b448c51821f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128027"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>Metoda ICorDebugProcess6::MarkDebuggerAttached
Zmienia stan wewnętrzny debugee tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> zwraca metody w bibliotece klas programu .NET Framework `true`.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fIsAttached`  
 `true` Jeśli <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metody powinny wskazywać, że jest dołączony debuger; `false` inaczej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda może zwracać wartości wymienione w poniższej tabeli.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|`S_OK`|Pomyślnie zaktualizowano debugowany program.|  
|`CORDBG_E_MODULE_NOT_LOADED`|Zestaw, który zawiera <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda nie jest załadowany lub inny błąd, takie jak Brak metadanych uniemożliwia jej rozpoznawane.<br /><br /> Ten błąd jest najczęściej i niegroźne. Należy wywołać metodę ponownie, gdy załadować dodatkowe zestawy.|  
|Inne niepowodzenia `HRESULT` wartości.|Inne wartości, które mogą wskazywać nieprawidłowo funkcjonującego debugera lub składniki kompilatora.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejs ICorDebugProcess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
