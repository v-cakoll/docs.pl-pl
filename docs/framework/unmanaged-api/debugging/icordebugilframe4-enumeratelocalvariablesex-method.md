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
ms.openlocfilehash: afeec3df03fc2b122ca8deb8123b79314b5e3837
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782420"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera moduł wyliczający dla zmiennej lokalnej w ramce i opcjonalnie zawiera zmienne dodane w instrumentacji profilera ReJIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 podczas Element członkowski wyliczenia [ILCodeKind](ilcodekind-enumeration.md) , który określa, czy zmienne dodane w Instrumentacji ReJIT profilera są zawarte w ramce.  
  
 `ppValueEnum`  
 określoną Wskaźnik do adresu obiektu "ICorDebugValueEnum", który jest modułem wyliczającym dla zmiennych lokalnych w tej ramce.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do metody [EnumerateLocalVariables —](icordebugilframe-enumeratelocalvariables-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennych dodanych w Instrumentacji ReJIT profilera. Ustawienie `flags` `ILCODE_ORIGINAL_IL` jest równoważne wywołaniu [ICorDebugILFrame:: EnumerateLocalVariables —](icordebugilframe-enumeratelocalvariables-method.md). Ustawienie `flags` na `ILCODE_REJIT_IL` pozwala debugerowi na dostęp do zmiennych lokalnych dodanych w Instrumentacji ReJIT profilera. Jeśli język pośredni (IL) nie ma instrumentacji, Wyliczenie jest puste, a metoda zwraca `S_OK`.  
  
 Moduł wyliczający nie może zawierać wszystkich zmiennych lokalnych w uruchomionej metodzie, ponieważ niektóre z nich mogą nie być aktywne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILFrame4, interfejs](icordebugilframe4-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [ReJIT: Przewodnik po poradniku](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
