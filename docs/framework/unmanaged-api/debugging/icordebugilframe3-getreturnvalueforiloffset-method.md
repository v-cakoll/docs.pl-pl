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
ms.openlocfilehash: 7ac90473a0bf15173683c45abc8e4a840ea7e733
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088304"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset — Metoda
Pobiera obiekt "ICorDebugValue", która hermetyzuje wartość zwracaną przez funkcję.  
  
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
 Wskaźnik na adres obiektu interfejsu "ICorDebugValue", który zawiera informacje o wartości zwracanego wywołania funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana wraz z [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metodę, aby uzyskać wartość zwracaną przez metodę. Jest to szczególnie użyteczne w przypadku metod, których wartości zwracane są ignorowane, jak poniższe dwa przykłady kodu. Pierwszy przykład wywołuje <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metody, ale ignoruje wartość zwracaną metody.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Drugi przykład przedstawia znacznie bardziej powszechny problem związany z debugowaniem. Ponieważ metoda jest używana jako argument w wywołaniu metody, jego wartość zwracana jest dostępna tylko wtedy, gdy debugger przeprowadza metodę wywołania. W wielu przypadkach szczególnie w przypadku, gdy wywoływana metoda jest zdefiniowana w zewnętrznej bibliotece, która nie jest możliwe.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 W przypadku przekazania [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metody przesunięcia języka pośredniego do witryny wywołania funkcji, zwraca jedno lub więcej przesunięć natywnych. Debuger może następnie ustawić punkty przerwania na tych macierzystych przesunięciach w funkcji. Kiedy debuger uderza w jeden z punktów przerwania, możesz następnie przekazać samo przesunięcie IL, które przekazałeś do tej metody, aby uzyskać wartość zwracaną. Debuger powinien następnie wyczyść wszystkie ustawione punkty przerwania.  
  
> [!WARNING]
>  [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) i `ICorDebugILFrame3::GetReturnValueForILOffset` metody umożliwiają uzyskanie informacji o wartości zwracanej tylko dla typów odwołania. Trwa pobieranie informacji o wartości zwracanej z typów wartości (czyli wszystkich typów, które wynikają z <xref:System.ValueType>) nie jest obsługiwane.  
  
 Przesunięcie IL określone przez `ILOffset` parametr powinien być wyświetlany witryny wywołania funkcji, a obiekt debugowany powinien zostać zatrzymany w punkcie przerwania ustawionym na przesunięciu macierzystym zwracanym przez [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) — metoda dla tego samego przesunięcia IL. Jeśli obiekt debugowany nie zostanie zatrzymany w poprawnej lokalizacji dla określonego przesunięcia języka Pośredniego, interfejs API nie powiedzie się.  
  
 Jeśli wywołanie funkcji nie zwraca wartości, interfejs API nie powiedzie się.  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset` Metoda jest dostępna tylko na podstawie x86 i AMD64 systemów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetReturnValueLiveOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
