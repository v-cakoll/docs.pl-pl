---
title: "ICorDebugILFrame3::GetReturnValueForILOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- csharp
- vb
api_name: ICorDebugILFrame3.GetReturnValueForILOffset
api_location: mscordbi.dll
api_type: COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c58319de99bdd8d7cce0ea55ccb3140a31a39bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset — Metoda
Pobiera obiekt hermetyzujący wartość zwracaną przez funkcję "ICorDebugValue".  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ILOffset`  
 Przesunięciu IL. W sekcji uwag.  
  
 `ppReturnValue`  
 Wskaźnik do adres obiektu interfejsu "ICorDebugValue", który zawiera informacje o wartość zwrotna z wywołania funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana wraz z [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metodę, aby pobrać wartość zwracaną przez metodę. Jest to szczególnie przydatne w przypadku których wartości zwracane są ignorowane, tak jak w poniższych przykładach kodu dwóch metod. Pierwsze wywołania przykład <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metody, ale ignoruje wartości zwracanej przez metodę.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Drugim przykładzie przedstawiono bardziej powszechny problem w debugowaniu. Ponieważ metoda jest używana jako argument w wywołaniu metody, jego wartości zwracanej jest dostępna tylko wtedy, gdy debuger przechodzi przez wywołaną metodę. W wielu przypadkach zwłaszcza w przypadku wywołaną metodę jest zdefiniowany w zewnętrznej biblioteki, który nie jest możliwe.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 W przypadku przekazania [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metody jako IL przesunięcie do lokacji wywołania funkcji, zwraca co najmniej jednego macierzystego przesunięcia. Debuger można następnie ustawić punkty przerwania w macierzystym przesunięcia w funkcji. Gdy debuger trafi jednego z punktów przerwania, można następnie przekazać tej samej przesunięciu IL, który został przekazany do tej metody można pobrać wartości zwracanej. Debuger należy następnie wyczyść wszystkie punkty przerwania, które go ustawić.  
  
> [!WARNING]
>  [ICorDebugCode3::GetReturnValueLiveOffset — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) i `ICorDebugILFrame3::GetReturnValueForILOffset` metody umożliwiają uzyskanie informacji zwracanej wartości dla typów referencyjnych tylko. Pobieranie informacji o wartości zwracanej z typów wartości (oznacza to, wszystkie typy, które pochodzą z <xref:System.ValueType>) nie jest obsługiwana.  
  
 Określone przez przesunięcie IL `ILOffset` parametr powinien być w witrynie wywołania funkcji, a obiekt debugowany powinna zostać zatrzymana na punkt przerwania ustawiony przy przesunięciu natywnego zwrócony przez [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) — metoda dla tego samego przesunięciu IL. Obiekt debugowany nie został on zatrzymany w poprawnej lokalizacji dla określonego przesunięcia IL, interfejsu API zakończy się niepowodzeniem.  
  
 Wywołanie funkcji nie zwraca wartości, interfejsu API zakończy się niepowodzeniem.  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset` Metoda jest dostępna tylko na podstawie x86 i systemy AMD64.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetReturnValueLiveOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [ICorDebugILFrame3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
