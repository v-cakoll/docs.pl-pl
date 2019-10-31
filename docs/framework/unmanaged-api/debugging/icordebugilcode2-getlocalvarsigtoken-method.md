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
ms.openlocfilehash: 243000a2399b4938a3ad7f732c64e2f79b664f51
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131060"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a>Metoda ICorDebugILCode2::GetLocalVarSigToken
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera token metadanych lokalnej zmiennej sygnatury dla funkcji reprezentowanej przez to wystąpienie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pmdSig`  
 określoną Wskaźnik do `mdSignature` token dla zmiennej lokalnej dla tej funkcji lub `mdSignatureNil`, jeśli nie ma sygnatury (czyli jeśli funkcja nie ma żadnych zmiennych lokalnych).  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILCode2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
