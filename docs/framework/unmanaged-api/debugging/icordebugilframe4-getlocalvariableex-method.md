---
title: Metoda ICorDebugILFrame4::GetLocalVariableEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: 017c14e9170087f3c3c9de64f50d165fc91aa297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782417"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>Metoda ICorDebugILFrame4::GetLocalVariableEx
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wartość określonej zmiennej lokalnej w ramce stosu języka pośredniego (IL) i opcjonalnie uzyskuje dostęp do zmiennej dodanej w instrumentacji profilera ReJIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 podczas Element członkowski wyliczenia [ILCodeKind](ilcodekind-enumeration.md) , który określa, czy zmienna dodana w Instrumentacji ReJIT profilera jest uwzględniona w ramce.  
  
 `dwIndex`  
 podczas Indeks zmiennej lokalnej w ramce stosu IL.  
  
 `ppValue`  
 określoną Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje pobraną wartość.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do metody [GetLocalVariable —](icordebugilframe-getlocalvariable-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennej dodanej w Instrumentacji ReJIT profilera. Wywołanie tej metody z `flags` wartością `ILCODE_ORIGINAL_IL` jest równoważne wywołaniu [GetLocalVariable —](icordebugilframe-getlocalvariable-method.md); Jeśli metoda jest Instrumentacją z dodatkowymi zmiennymi lokalnymi, nie można uzyskać dostępu do tych zmiennych. `ILCODE_REJIT_IL` pozwala debugerowi na dostęp do zmiennych lokalnych dodanych w Instrumentacji ReJIT profilera. Jeśli IL nie jest Instrumentacją, metoda zwraca `E_INVALIDARG`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILFrame4, interfejs](icordebugilframe4-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [ReJIT: Przewodnik po poradniku](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
