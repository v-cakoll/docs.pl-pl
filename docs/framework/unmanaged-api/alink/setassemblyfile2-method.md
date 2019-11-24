---
title: SetAssemblyFile2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 4f710ef9741869a2b4fd8473ed3ecf379cfcc56d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445582"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 — Metoda
Sets the name of and options for a new assembly. Do not call this method when you produce unbound modules.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 Name of manifest file.  
  
 `pEmitter`  
 [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.  
  
 `afFlags`  
 Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Receives unique ID for the assembly being constructed.  
  
## <a name="return-value"></a>Wartość zwracana  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Wymagania  
 Requires alink.h.  
  
## <a name="see-also"></a>Zobacz także

- [IALink2, interfejs](ialink2-interface.md)
- [IALink, interfejs](ialink-interface.md)
- [ALink, interfejs API](index.md)
