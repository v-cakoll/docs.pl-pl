---
title: SetAssemblyFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d341aca7c96e5932a1fc155ccaee17ce6585da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777005"
---
# <a name="setassemblyfile-method"></a>SetAssemblyFile — Metoda
Przypisuje nazwę zestawu, który ma zostać skompilowany. Nie do użycia podczas tworzenia niezwiązanych modułów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 W pełni kwalifikowana nazwa pliku manifestu.  
  
 `pEmitter`  
 Wskaźnik do interfejsu [interfejsu IMetaDataEmit](../metadata/imetadataemit-interface.md) .  
  
 `afFlags`  
 Flagi zgodnie z definicją w [wyliczeniu AssemblyFlags —](../metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Wskaźnik na identyfikator tworzonego zestawu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h.  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
