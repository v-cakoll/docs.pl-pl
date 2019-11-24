---
title: SetPEKind — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: dfbc10bdbe633450dee2e27524c29ead21fb739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445533"
---
# <a name="setpekind-method"></a>SetPEKind — Metoda
Determines the portable executable type, either machine-specific or machine-agnostic.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID of the assembly.  
  
 `FileToken`  
 Token of file for which the PE type is to be set. Can be NULL if `AssemblyID` does not indicate an unbound netmodule.  
  
 `dwPEKind`  
 The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 The target machine architecture, as indicated in the NT header.  
  
## <a name="return-value"></a>Wartość zwracana  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Wymagania  
 Requires alink.h.  
  
## <a name="see-also"></a>Zobacz także

- [GetPEKind, metoda](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2, interfejs](ialink2-interface.md)
- [IALink, interfejs](ialink-interface.md)
- [ALink, interfejs API](index.md)
