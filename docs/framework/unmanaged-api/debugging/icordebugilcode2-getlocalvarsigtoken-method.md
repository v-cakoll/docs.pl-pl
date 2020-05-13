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
ms.openlocfilehash: 3b9c2f0e20488826aca202b3ef454104964b8bb9
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210348"
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
 określoną Wskaźnik do `mdSignature` tokenu dla zmiennej lokalnej dla tej funkcji lub `mdSignatureNil` Jeśli nie ma podpisu (oznacza to, że funkcja nie ma żadnych zmiennych lokalnych).  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejs ICorDebugILCode2](icordebugilcode2-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
