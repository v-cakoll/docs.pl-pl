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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03ee275336d3ae71f63d82add694fe1308efbe8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125940"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset — Metoda
Dla określonego przesunięcia języka Pośredniego pobiera natywne przesunięcia, w której punkt przerwania powinien znajdować się tak, że debugger może uzyskać wartość zwracaną przez funkcję.  
  
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
 Przesunięcie IL. Musi być witryną wywołania funkcji lub wywołanie funkcji zakończy się niepowodzeniem.  
  
 `bufferSize`  
 Liczba bajtów dostępnych do przechowywania `pOffsets`.  
  
 `pFetched`  
 Wskaźnik liczby przesunięć rzeczywistego. Zwykle, jego wartość wynosi 1, ale pojedyncza instrukcja IL można mapować do wielu `CALL` instrukcje zestawu.  
  
 `pOffsets`  
 Tablica macierzystego przesunięcia. Zazwyczaj `pOffsets` zawiera pojedyncze przesunięcie, mimo że pojedyncza instrukcja IL może mapować do wielu mapowań do wielu `CALL` instrukcje zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana wraz z [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metodę, aby uzyskać wartość zwracaną przez metodę, która zwraca typ odwołania. Przekazywanie przesunięcia języka Pośredniego do witryny wywołania funkcji do tej metody zwraca jedno lub więcej przesunięć natywnych. Debuger może następnie ustawić punkty przerwania na tych macierzystych przesunięciach w funkcji. Kiedy debuger uderza w jeden z punktów przerwania, możesz następnie przekazać samo przesunięcie IL, które przekazałeś do tej metody do [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metodę, aby uzyskać wartość zwracaną. Debuger powinien następnie wyczyść wszystkie ustawione punkty przerwania.  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset` i [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metody umożliwiają uzyskanie informacji o wartości zwracanej tylko dla typów odwołania. Trwa pobieranie informacji o wartości zwracanej z typów wartości (czyli wszystkich typów, które wynikają z <xref:System.ValueType>) nie jest obsługiwane.  
  
 Funkcja zwraca `HRESULT` wartości podanych w poniższej tabeli.  
  
|`HRESULT` value|Opis|  
|---------------------|-----------------|  
|`S_OK`|Powodzenie.|  
|`CORDBG_E_INVALID_OPCODE`|Podanego przesunięcia IL nie jest instrukcją call, lub funkcja zwraca `void`.|  
|`CORDBG_E_UNSUPPORTED`|Podane przesunięcie IL jest odpowiednim wywołaniem, ale zwracany typ nie jest obsługiwany dla uzyskania wartości zwracanej.|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset` Metoda jest dostępna tylko na podstawie x86 i AMD64 systemów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetReturnValueForILOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
