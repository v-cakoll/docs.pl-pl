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
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178814"
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
 Wskaźnik do adresu obiektu interfejsu "ICorDebugValue", który zawiera informacje o wartości zwracanej wywołania funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana wraz z [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) metody, aby uzyskać wartość zwracaną metody. Jest to szczególnie przydatne w przypadku metod, których zwracane wartości są ignorowane, jak w następujących dwóch przykładach kodu. Pierwszy przykład wywołuje <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodę, ale ignoruje wartość zwracaną metody.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Drugi przykład ilustruje znacznie bardziej typowy problem podczas debugowania. Ponieważ metoda jest używana jako argument w wywołaniu metody, jego zwracana wartość jest dostępna tylko wtedy, gdy debuger postępuje przez metodę wywoływaną. W wielu przypadkach, szczególnie gdy wywoływana metoda jest zdefiniowana w bibliotece zewnętrznej, nie jest to możliwe.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Jeśli przekażesz [metodę ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) przesunięcie IL do witryny wywołania funkcji, zwraca jedno lub więcej natywnych przesunięć. Debuger można następnie ustawić punkty przerwania na tych przesunięciach natywnych w funkcji. Gdy debuger trafi jeden z punktów przerwania, można następnie przekazać to samo przesunięcie IL, które zostało przekazane do tej metody, aby uzyskać wartość zwracaną. Debuger powinien następnie wyczyścić wszystkie punkty przerwania, które go ustawić.  
  
> [!WARNING]
> [ICorDebugCode3::GetReturnValueLiveOffset Metoda](icordebugcode3-getreturnvalueliveoffset-method.md) `ICorDebugILFrame3::GetReturnValueForILOffset` i metody pozwalają uzyskać informacje o wartości zwracanej tylko dla typów odwołań. Pobieranie informacji o wartości zwracanej z typów wartości (czyli wszystkich typów, które wynikają z <xref:System.ValueType>) nie jest obsługiwane.  
  
 Przesunięcie IL określone `ILOffset` przez parametr powinien znajdować się w lokacji wywołania funkcji, a debuggee powinny być zatrzymane w zestawie przerwania na natywnym przesunięciu zwróconym przez metodę [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) dla tego samego przesunięcia IL. Jeśli debuggee nie zostanie zatrzymana w odpowiedniej lokalizacji dla określonego przesunięcia IL, interfejs API zakończy się niepowodzeniem.  
  
 Jeśli wywołanie funkcji nie zwraca wartości, interfejs API zakończy się niepowodzeniem.  
  
 Metoda `ICorDebugILFrame3::GetReturnValueForILOffset` jest dostępna tylko w systemach opartych na architekturze x86 i AMD64.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetReturnValueLiveOffset, metoda](icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3, interfejs](icordebugilframe3-interface.md)
