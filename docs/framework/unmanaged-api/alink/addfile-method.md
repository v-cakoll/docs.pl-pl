---
title: AddFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
ms.openlocfilehash: 4dd104805d547613315335bc9c95b5c60a9cab14
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446686"
---
# <a name="addfile-method"></a>AddFile — Metoda
Dodaje pliki do zestawu. Może również służyć do tworzenia niezwiązanych modułów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Unikatowy identyfikator zestawu, który ma zostać rozszerzony.  
  
 `pszFilename`  
 W pełni kwalifikowana nazwa pliku, który ma zostać dodany.  
  
 `dwFlags`  
 Flagi FileDef modelu COM+, takie jak `ffContainsNoMetaData` i `ffWriteable`. `dwFlags` jest przenoszona do [metody DefineFile —](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Interfejs [interfejsu IMetaDataEmit](../metadata/imetadataemit-interface.md) , który ma być używany do emitowania metadanych, w razie potrzeby.  
  
 `pFileToken`  
 Wskaźnik do lokalizacji, w której będzie przechowywany unikatowy identyfikator dodanego pliku.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h.  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
