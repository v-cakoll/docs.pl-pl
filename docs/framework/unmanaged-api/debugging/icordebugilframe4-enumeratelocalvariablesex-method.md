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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3deb497c3e842e25bcaa46a867dd61ea4a1c3804
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926817"
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
 podczas Element członkowski wyliczenia [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , który określa, czy zmienne dodane w Instrumentacji ReJIT profilera są zawarte w ramce.  
  
 `ppValueEnum`  
 określoną Wskaźnik do adresu obiektu "ICorDebugValueEnum", który jest modułem wyliczającym dla zmiennych lokalnych w tej ramce.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do metody [EnumerateLocalVariables —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennych dodanych w Instrumentacji ReJIT profilera. Ustawienie `flags` jest równoważne wywołaniu [ICorDebugILFrame:: EnumerateLocalVariables —.](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) `ILCODE_ORIGINAL_IL` Ustawienie `flags`pozwaladebugerowi nadostępdozmiennychlokalnychdodanychwInstrumentacjiReJITprofilera.`ILCODE_REJIT_IL` Jeśli język pośredni (IL) nie ma instrumentacji, Wyliczenie jest puste i metoda zwraca `S_OK`.  
  
 Moduł wyliczający nie może zawierać wszystkich zmiennych lokalnych w uruchomionej metodzie, ponieważ niektóre z nich mogą nie być aktywne.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILFrame4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Przewodnik krok po kroku](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
