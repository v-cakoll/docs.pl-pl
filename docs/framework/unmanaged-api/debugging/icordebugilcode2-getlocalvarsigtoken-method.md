---
title: Metoda ICorDebugILCode2::GetLocalVarSigToken
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e02f44e4f581170a842a1c103ed069cb90cde79c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412301"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a>Metoda ICorDebugILCode2::GetLocalVarSigToken
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera token metadanych dla zmiennej podpisu lokalnego dla funkcji, która jest reprezentowana przez to wystąpienie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pmdSig`  
 [out] Wskaźnik do `mdSignature` tokenu dla zmiennej podpisu lokalnego dla tej funkcji, lub `mdSignatureNil` Jeśli nie istnieje sygnatura nie (Jeśli funkcja nie ma żadnych zmiennych lokalnych).  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugILCode2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
