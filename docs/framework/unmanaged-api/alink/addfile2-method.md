---
title: AddFile2 — Metoda
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: 8dadf9ec8f896b03e4918b21f5153c1b747010fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446664"
---
# <a name="addfile2-method"></a>AddFile2 — Metoda
Dodaje pliki do zestawu. Może również służyć do tworzenia niezwiązanych modułów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu, do którego zostanie dodany plik.  
  
 `pszFilename`  
 Nazwa pliku, który ma zostać dodany.  
  
 `dwFlags`  
 Flagi `FileDef` COM+, takie jak `ffContainsNoMetaData` i `ffWriteable`. `dwFlags` jest przenoszona do [metody DefineFile —](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Interfejs do interfejsu [interfejsu IMetaDataEmit2](../metadata/imetadataemit2-interface.md) .  
  
 `pFileToken`  
 Odbiera identyfikator dodawanego pliku.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h.  
  
## <a name="see-also"></a>Zobacz także

- [IALink2, interfejs](ialink2-interface.md)
- [IALink, interfejs](ialink-interface.md)
- [ALink, interfejs API](index.md)
