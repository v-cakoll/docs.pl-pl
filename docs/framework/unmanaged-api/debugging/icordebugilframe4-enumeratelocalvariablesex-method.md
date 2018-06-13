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
ms.openlocfilehash: 49d2a0955f9ef0c54a8953971ce3671ce16d3b85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418932"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera moduł wyliczający dla zmiennej lokalnej w ramce i opcjonalnie zawiera zmienne dodane w ReJIT Instrumentacji profilera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 [in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) element członkowski wyliczenia, która określa, czy zmienne dodane w ReJIT Instrumentacji profilera znajdują się w ramce.  
  
 `ppValueEnum`  
 [out] Wskaźnik do adres obiektu "ICorDebugValueEnum", który moduł wyliczający dla zmiennych lokalnych w tej ramce.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) metody, z wyjątkiem, że opcjonalnie dostęp do zmiennych dodane w ReJIT Instrumentacji profilera. Ustawienie `flags` do `ILCODE_ORIGINAL_IL` jest odpowiednikiem wywołania [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md). Ustawienie `flags` do `ILCODE_REJIT_IL` umożliwia debugera tak, aby mieć dostęp do zmiennych lokalnych dodane w ReJIT Instrumentacji profilera. Jeśli nie został zinstrumentowany na języku pośrednim (IL), wyliczenie jest pusty i metoda zwraca `S_OK`.  
  
 Moduł wyliczający nie może zawierać wszystkich zmiennych lokalnych w metodzie uruchomione, ponieważ niektóre z nich nie może być aktywny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugILFrame4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Przewodnik](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
