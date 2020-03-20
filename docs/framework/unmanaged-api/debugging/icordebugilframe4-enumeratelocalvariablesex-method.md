---
title: Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: 341a86f4c1c8367f979e193a6284bf89f1b03ca0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178801"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera moduł wyliczania dla zmiennej lokalnej w ramce i opcjonalnie zawiera zmienne dodane w profiler instrumentacji ReJIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 [w] Element członkowski wyliczenia [ILCodeKind,](ilcodekind-enumeration.md) który określa, czy zmienne dodane w instrumentacji ReJIT profilera są zawarte w ramce.  
  
 `ppValueEnum`  
 [na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugValueEnum", który jest wyliczaczem zmiennych lokalnych w tej ramce.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do [Metody EnumerateLocalVariables,](icordebugilframe-enumeratelocalvariables-method.md) z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennych dodanych w instrumentacji ReJIT profilera. Ustawienie `flags` `ILCODE_ORIGINAL_IL` jest równoważne wywołaniu [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md). `flags` Ustawienie, `ILCODE_REJIT_IL` aby umożliwia debugerowi dostęp do zmiennych lokalnych dodanych w profiler Instrumentacji ReJIT. Jeśli język pośredni (IL) nie jest instrumentowany, wyliczenie `S_OK`jest puste, a metoda zwraca .  
  
 Wyliczacz może nie zawierać wszystkie zmienne lokalne w uruchomionej metody, ponieważ niektóre z nich mogą nie być aktywne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugILFrame4, interfejs](icordebugilframe4-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [ReJIT: Poradnik](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
