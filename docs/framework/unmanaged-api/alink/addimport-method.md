---
title: AddImport — Metoda
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aed70a78e2513f4d63fbf8ca8868f26efbac9ae8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787663"
---
# <a name="addimport-method"></a>AddImport — Metoda
Dodaje Importy do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Unikatowy identyfikator zestawu, który ma zostać rozszerzony.  
  
 `ImportToken`  
 Unikatowy identyfikator, pobrany z [metody ImportFile —](importfile-method.md), pliku do zaimportowania.  
  
 `dwFlags`  
 Flagi FileDef modelu COM+, `ffContainsNoMetaData` takie `ffWriteable`jak i. `dwFlags`jest przenoszona do [metody DefineFile —](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Wskaźnik do tokenu, który odbiera identyfikator dla tworzonego pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
