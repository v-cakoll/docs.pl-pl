---
title: Metoda ICorDebugILFrame4::GetCodeEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: e77344a99189ec8e234129262d45698c794dc249
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788513"
---
# <a name="icordebugilframe4getcodeex-method"></a>Metoda ICorDebugILFrame4::GetCodeEx
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wskaźnik do kodu, który jest wykonywany przez tę ramkę stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 podczas Element członkowski wyliczenia [ILCodeKind](ilcodekind-enumeration.md) , który określa, czy język pośredni (IL) zdefiniowany przez żądanie ReJIT profilera zostanie uwzględniony w ramce.  
  
 `ppCode`  
 określoną Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje kod, który jest wykonywany przez tę ramkę stosu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do metody [ICorDebugFrame:: GetCode](icordebugframe-getcode-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do kodu zdefiniowanego przez żądanie ReJIT profilera. Wywołanie tej metody z `flags` wartością `ILCODE_ORIGINAL_IL` jest równoważne wywołaniu metody [GetCode](icordebugframe-getcode-method.md); Jeśli metoda jest Instrumentacją, jej kod IL nie będzie dostępny. `ILCODE_REJIT_IL` zezwala debugerowi na dostęp do IL zdefiniowanego przez żądanie ReJIT profilera. Jeśli IL nie ma instrumentacji, `ppCode` ma **wartość null**, a metoda zwraca `S_OK`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILFrame4, interfejs](icordebugilframe4-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [ReJIT: Przewodnik po poradniku](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
