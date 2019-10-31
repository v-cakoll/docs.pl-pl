---
title: ICorDebugCode3::GetReturnValueLiveOffset — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 77cda2c3d30b5926da219a38b762295818ca54a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121194"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset — Metoda
W przypadku określonego przesunięcia IL pobiera natywne przesunięcia, w których powinien być umieszczony punkt przerwania, aby debuger mógł uzyskać wartość zwracaną z funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ILoffset`  
 Przesunięcie IL. Musi to być witryna wywołania funkcji lub wywołanie funkcji zakończy się niepowodzeniem.  
  
 `bufferSize`  
 Liczba bajtów dostępnych do przechowywania `pOffsets`.  
  
 `pFetched`  
 Wskaźnik do liczby zwróconych przesunięć. Zazwyczaj jego wartość wynosi 1, ale Pojedyncza instrukcja IL może mapować na wiele `CALL` instrukcji zestawu.  
  
 `pOffsets`  
 Tablica przesunięć natywnych. Zwykle `pOffsets` zawiera pojedyncze przesunięcie, chociaż Pojedyncza instrukcja IL może mapować na wiele map do wielu `CALL` instrukcji zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana razem z metodą [ICorDebugILFrame3:: GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) w celu uzyskania wartości zwracanej przez metodę zwracającą typ referencyjny. Przekazywanie przesunięcia IL do witryny wywołania funkcji do tej metody zwraca jedno lub więcej natywnych przesunięć. Debuger może następnie ustawić punkty przerwania dla tych natywnych przesunięć w funkcji. Gdy debuger trafi jeden z punktów przerwania, można następnie przekazać to samo przesunięcie IL przekazane do tej metody do metody [ICorDebugILFrame3:: GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) w celu uzyskania wartości zwracanej. Debuger powinien następnie wyczyścić wszystkie ustawione punkty przerwania.  
  
> [!WARNING]
> Metody `ICorDebugCode3::GetReturnValueLiveOffset` i [ICorDebugILFrame3:: GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) umożliwiają uzyskanie informacji o wartości zwracanej tylko dla typów referencyjnych. Pobieranie informacji o wartości zwracanej z typów wartości (to oznacza, że wszystkie typy pochodne od <xref:System.ValueType>) nie są obsługiwane.  
  
 Funkcja zwraca wartości `HRESULT` pokazane w poniższej tabeli.  
  
|wartość `HRESULT`|Opis|  
|---------------------|-----------------|  
|`S_OK`|Prawnego.|  
|`CORDBG_E_INVALID_OPCODE`|Dana witryna przesunięcia IL nie jest instrukcją wywołania lub funkcja zwraca `void`.|  
|`CORDBG_E_UNSUPPORTED`|Określone przesunięcie IL jest właściwym wywołaniem, ale zwracany typ nie jest obsługiwany przez pobranie wartości zwracanej.|  
  
 Metoda `ICorDebugCode3::GetReturnValueLiveOffset` jest dostępna tylko w systemach opartych na architekturze x86 i AMD64.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetReturnValueForILOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
