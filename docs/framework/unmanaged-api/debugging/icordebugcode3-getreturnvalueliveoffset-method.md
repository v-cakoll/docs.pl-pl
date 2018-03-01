---
title: "ICorDebugCode3::GetReturnValueLiveOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d10d298a031e7146eaf6cf7988538e6f7020136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset — Metoda
Określony przesunięcia IL pobiera natywnego przesunięcia gdzie ma zostać umieszczony punkt przerwania, aby debuger można uzyskać wartości zwracanej przez funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ILoffset`  
 Przesunięciu IL. Musi to być witryna wywołania funkcji lub wywołanie funkcji zakończy się niepowodzeniem.  
  
 `bufferSize`  
 Liczba bajtów dostępne do przechowywania `pOffsets`.  
  
 `pFetched`  
 Wskaźnik do liczba przesunięć faktycznie zwracane. Zwykle, jego wartość wynosi 1, ale pojedynczej instrukcji IL można mapować do wielu `CALL` instrukcje zestawu.  
  
 `pOffsets`  
 Tablica natywnego przesunięcia. Zazwyczaj `pOffsets` zawiera pojedynczy przesunięcie, mimo że pojedyncza instrukcja IL można mapować do mapy wiele do wielu `CALL` instrukcje zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana wraz z [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metodę, aby pobrać wartość zwracaną przez metodę, która zwraca typ referencyjny. Przekazywanie IL przesunięcie do witryny wywołania funkcji, aby ta metoda zwraca co najmniej jednego macierzystego przesunięcia. Debuger można następnie ustawić punkty przerwania w macierzystym przesunięcia w funkcji. Gdy debuger trafi jednego z punktów przerwania, można następnie przekazać tej samej przesunięciu IL, który został przekazany do tej metody do [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metody można pobrać wartości zwracanej. Debuger należy następnie wyczyść wszystkie punkty przerwania, które go ustawić.  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset` i [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metody umożliwiają uzyskanie informacji zwracanej wartości dla typów referencyjnych tylko. Pobieranie informacji o wartości zwracanej z typów wartości (oznacza to, wszystkie typy, które pochodzą z <xref:System.ValueType>) nie jest obsługiwana.  
  
 Funkcja zwraca `HRESULT` wartości podanych w poniższej tabeli.  
  
|`HRESULT`wartość|Opis|  
|---------------------|-----------------|  
|`S_OK`|Powodzenie.|  
|`CORDBG_E_INVALID_OPCODE`|Daną witrynę przesunięcia IL nie jest instrukcja wywołania lub funkcja zwraca `void`.|  
|`CORDBG_E_UNSUPPORTED`|Danym przesunięciu IL jest odpowiednie połączenie, ale zwracany typ nie jest obsługiwany dla pobierania wartości zwracanej.|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset` Metoda jest dostępna tylko na podstawie x86 i systemy AMD64.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetReturnValueForILOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [ICorDebugCode3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
