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
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178791"
---
# <a name="icordebugilframe4getcodeex-method"></a>Metoda ICorDebugILFrame4::GetCodeEx
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wskaźnik do kodu, który wykonuje tę ramkę stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 [w] Element członkowski wyliczania [ILCodeKind,](ilcodekind-enumeration.md) który określa, czy język pośredni (IL) zdefiniowany przez żądanie ReJIT profilera znajduje się w ramce.  
  
 `ppCode`  
 [na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje kod, który wykonuje tę ramkę stosu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do [metody ICorDebugFrame::GetCode,](icordebugframe-getcode-method.md) z tą różnicą, że opcjonalnie uzyskuje dostęp do kodu zdefiniowanego przez żądanie ReJIT profilera. Wywołanie tej `flags` metody `ILCODE_ORIGINAL_IL` o wartości jest równoważne wywołaniu [GetCode;](icordebugframe-getcode-method.md) jeśli metoda jest oprzyrządowana, jej IL nie będzie dostępny. `ILCODE_REJIT_IL`umożliwia debugerowi dostęp do identyfikatora IL zdefiniowanego przez żądanie ReJIT profilera. Jeśli IL nie jest `ppCode` instrumentowany, ma wartość `S_OK` **null**, a metoda zwraca .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugILFrame4, interfejs](icordebugilframe4-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [ReJIT: Poradnik](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
