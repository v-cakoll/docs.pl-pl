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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb4eaaa23a810a23852dc5ef88d61c6a5d0f0ccd
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926806"
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
 podczas Element członkowski wyliczenia [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , który określa, czy zmienna dodana w Instrumentacji ReJIT profilera jest uwzględniona w ramce.  
  
 `dwIndex`  
 podczas Indeks zmiennej lokalnej w ramce stosu IL.  
  
 `ppValue`  
 określoną Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje pobraną wartość.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do metody [GetLocalVariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennej dodanej w Instrumentacji ReJIT profilera. Wywołanie tej metody z `flags` `ILCODE_ORIGINAL_IL` wartością jest równoznaczne z wywołaniem metody [GetLocalVariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Jeśli metoda jest Instrumentacją przy użyciu dodatkowych zmiennych lokalnych, nie można uzyskać dostępu do tych zmiennych. `ILCODE_REJIT_IL`zezwala debugerowi na dostęp do zmiennych lokalnych dodanych w Instrumentacji ReJIT profilera. Jeśli IL nie jest Instrumentacją, metoda zwraca `E_INVALIDARG`.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILFrame4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Przewodnik krok po kroku](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
