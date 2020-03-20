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
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178940"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset — Metoda
Dla określonego przesunięcia IL pobiera natywne przesunięcia, gdzie punkt przerwania powinny być umieszczone tak, aby debuger można uzyskać wartość zwracaną z funkcji.  
  
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
 Przesunięcie IL. Musi to być lokacja wywołania funkcji lub wywołanie funkcji zakończy się niepowodzeniem.  
  
 `bufferSize`  
 Liczba bajtów dostępnych `pOffsets`do zapisania .  
  
 `pFetched`  
 Wskaźnik do liczby przesunięć faktycznie zwrócone. Zazwyczaj jego wartość wynosi 1, ale pojedyncza instrukcja IL można mapować do wielu `CALL` instrukcji zestawu.  
  
 `pOffsets`  
 Tablica natywnych przesunięć. Zazwyczaj `pOffsets` zawiera pojedyncze przesunięcie, chociaż pojedyncza instrukcja IL `CALL` można mapować do wielu map do wielu instrukcji zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana wraz z [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) metody, aby uzyskać wartość zwracaną metody, która zwraca typ odwołania. Przekazywanie przesunięcia IL do lokacji wywołania funkcji do tej metody zwraca jedno lub więcej natywnych przesunięć. Debuger można następnie ustawić punkty przerwania na tych przesunięciach natywnych w funkcji. Gdy debuger trafi jeden z punktów przerwania, można następnie przekazać to samo przesunięcie IL, które zostało przekazane do tej metody do [metody ICorDebugILFrame3::GetReturnValueForILOffset,](icordebugilframe3-getreturnvalueforiloffset-method.md) aby uzyskać wartość zwracaną. Debuger powinien następnie wyczyścić wszystkie punkty przerwania, które go ustawić.  
  
> [!WARNING]
> I `ICorDebugCode3::GetReturnValueLiveOffset` [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) metody pozwalają uzyskać informacje o wartości zwracanej tylko dla typów odwołań. Pobieranie informacji o wartości zwracanej z typów wartości (czyli wszystkich typów, które wynikają z <xref:System.ValueType>) nie jest obsługiwane.  
  
 Funkcja zwraca `HRESULT` wartości pokazane w poniższej tabeli.  
  
|`HRESULT`Wartość|Opis|  
|---------------------|-----------------|  
|`S_OK`|Powodzenie.|  
|`CORDBG_E_INVALID_OPCODE`|Dana witryna przesunięcia IL nie jest `void`instrukcją wywołania lub funkcja zwraca .|  
|`CORDBG_E_UNSUPPORTED`|Podane przesunięcie IL jest prawidłowym wywołaniem, ale typ zwracany nie jest obsługiwane dla uzyskania wartości zwracanej.|  
  
 Metoda `ICorDebugCode3::GetReturnValueLiveOffset` jest dostępna tylko w systemach opartych na architekturze x86 i AMD64.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetReturnValueForILOffset, metoda](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3, interfejs](icordebugcode3-interface.md)
