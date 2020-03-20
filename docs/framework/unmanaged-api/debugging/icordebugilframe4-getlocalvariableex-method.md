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
ms.openlocfilehash: ee263e8c49cd6da7278bd2299557336629720d2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178775"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>Metoda ICorDebugILFrame4::GetLocalVariableEx
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wartość określonej zmiennej lokalnej w tej ramce stosu języka pośredniego (IL) i opcjonalnie uzyskuje dostęp do zmiennej dodanej w instrumentacji ReJIT profilera.  
  
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
 [w] Element członkowski wyliczenia [ILCodeKind,](ilcodekind-enumeration.md) który określa, czy zmienna dodana w instrumentacji ReJIT profilera jest zawarta w ramce.  
  
 `dwIndex`  
 [w] Indeks zmiennej lokalnej w ramce stosu IL.  
  
 `ppValue`  
 [na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje pobraną wartość.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) metody, z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennej dodanej w profiler Instrumentacji ReJIT. Wywołanie tej `flags` metody `ILCODE_ORIGINAL_IL` o wartości jest równoznaczne z wywołaniem [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); jeśli metoda jest instrumentowana z dodatkowymi zmiennymi lokalnymi, nie można uzyskać dostępu do tych zmiennych. `ILCODE_REJIT_IL`umożliwia debugerowi dostęp do zmiennych lokalnych dodanych w instrumentacji ReJIT profilera. Jeśli IL nie jest instrumentowany, `E_INVALIDARG`metoda zwraca .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugILFrame4, interfejs](icordebugilframe4-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [ReJIT: Poradnik](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
