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
ms.openlocfilehash: 18a6154ad3fe3ee384a38007ab371e83482193ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545978"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>Metoda ICorDebugILFrame4::GetLocalVariableEx
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wartość określonej zmiennej lokalnej w tej ramce stosu języka pośredniego (IL), a opcjonalnie uzyskuje dostęp do zmiennej dodane w profilerze ReJIT instrumentacji.  
  
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
 [in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) składowej wyliczenia, która określa, czy zmienna dodany do programu profilującego Instrumentację ReJIT znajduje się w ramce.  
  
 `dwIndex`  
 [in] Indeks zmiennej lokalnej w ramce stosu IL.  
  
 `ppValue`  
 [out] Wskaźnik na adres "ICorDebugValue" obiekt, który reprezentuje pobraną wartość.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do [getlocalvariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody, z wyjątkiem tego opcjonalnie uzyskuje dostęp zmienną dodane w profilerze ReJIT instrumentacji. Wywołanie tej metody za pomocą `flags` wartość `ILCODE_ORIGINAL_IL` jest równoważne z wywoływaniem [getlocalvariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Jeśli metoda jest wyposażone w dodatkowe zmienne lokalne, nie można uzyskać dostępu do tych zmiennych. `ILCODE_REJIT_IL` Pozwala debugerowi, aby uzyskać dostęp do zmiennych lokalnych, dodane w profilerze ReJIT instrumentacji. Jeśli nie ma instrumentacji IL, metoda zwraca `E_INVALIDARG`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugILFrame4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Przewodniku z instrukcjami](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
