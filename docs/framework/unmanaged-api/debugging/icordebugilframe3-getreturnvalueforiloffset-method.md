---
title: ICorDebugILFrame3::GetReturnValueForILOffset — Metoda
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5832ec095ea0e96327f6a9636193da9c0c8a5dd2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988263"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset — Metoda
Pobiera obiekt "ICorDebugValue", który hermetyzuje zwracaną wartość funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ILOffset`  
 Przesunięcie IL. Zobacz sekcję Uwagi.  
  
 `ppReturnValue`  
 Wskaźnik do adresu obiektu interfejsu "ICorDebugValue", który zawiera informacje o zwracanej wartości wywołania funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana razem z metodą [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) w celu uzyskania wartości zwracanej przez metodę. Jest to szczególnie przydatne w przypadku metod, których wartości zwracane są ignorowane, jak w poniższych dwóch przykładach kodu. Pierwszy przykład wywołuje <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodę, ale ignoruje wartość zwracaną metody.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Drugi przykład ilustruje znacznie bardziej typowy problem w debugowaniu. Ponieważ metoda jest używana jako argument w wywołaniu metody, jego wartość zwracana jest dostępna tylko wtedy, gdy debuger przeprowadzi procedurę przez wywołaną metodę. W wielu przypadkach, szczególnie gdy wywołana metoda jest zdefiniowana w zewnętrznej bibliotece, która nie jest możliwa.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 W przypadku przekazania metody [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) przesunięcie Il do witryny wywołania funkcji zwraca jedno lub więcej przesunięć natywnych. Debuger może następnie ustawić punkty przerwania dla tych natywnych przesunięć w funkcji. Gdy debuger trafi jeden z punktów przerwania, można następnie przekazać to samo przesunięcie IL przekazane do tej metody w celu uzyskania wartości zwracanej. Debuger powinien następnie wyczyścić wszystkie ustawione punkty przerwania.  
  
> [!WARNING]
> Metody i `ICorDebugILFrame3::GetReturnValueForILOffset` metody [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) umożliwiają uzyskanie informacji o wartości zwracanej tylko dla typów referencyjnych. Pobieranie informacji o wartości zwracanej z typów wartości (to oznacza, że wszystkie typy <xref:System.ValueType>pochodne od) nie są obsługiwane.  
  
 Przesunięcie Il określone przez `ILOffset` parametr powinno znajdować się w witrynie wywołania funkcji, a debugowanego obiektu powinna zostać zatrzymana w punkcie przerwania ustawionym w natywnym przesunięciu zwróconym przez metodę [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) dla tego samego przesunięcia Il. Jeśli debugowanego obiektu nie zostanie zatrzymana w prawidłowej lokalizacji określonego przesunięcia IL, interfejs API nie powiedzie się.  
  
 Jeśli wywołanie funkcji nie zwraca wartości, interfejs API nie powiedzie się.  
  
 Ta `ICorDebugILFrame3::GetReturnValueForILOffset` Metoda jest dostępna tylko w systemach opartych na architekturze x86 i amd64.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetReturnValueLiveOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
