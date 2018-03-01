---
title: Metoda ICorDebugILFrame4::GetLocalVariableEx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 968e504eadb5f7444095a6a98dea414aa4486dce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>Metoda ICorDebugILFrame4::GetLocalVariableEx
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wartość zmiennej lokalnej określony w tej ramki stosu w języku pośrednim (IL) i opcjonalnie uzyskuje dostęp do zmiennej dodane w ReJIT Instrumentacji profilera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 [in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) element członkowski wyliczenia, która określa, czy zmienna dodane w ReJIT Instrumentacji profilera znajduje się w ramce.  
  
 `dwIndex`  
 [in] Indeks zmiennej lokalnej w ramce stosu IL.  
  
 `ppValue`  
 [out] Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje pobrana wartość.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody, z wyjątkiem, że opcjonalnie dostęp do zmiennej dodane w ReJIT Instrumentacji profilera. Wywołanie tej metody za pomocą `flags` wartość `ILCODE_ORIGINAL_IL` jest odpowiednikiem wywołania [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); w wypadku metody są instrumentowane przy użyciu dodatkowych zmiennych lokalnych, nie można uzyskać dostępu do tych zmiennych. `ILCODE_REJIT_IL`Umożliwia debugera tak, aby mieć dostęp do zmiennych lokalnych dodane w ReJIT Instrumentacji profilera. Jeśli nie ma instrumentacji IL, metoda zwraca `E_INVALIDARG`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugILFrame4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Przewodnik](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
