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
ms.openlocfilehash: bbe8a43f44d59249abc713c95fce31f1fb9a5993
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148671"
---
# <a name="addimport-method"></a>AddImport — Metoda
Importy dodaje do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Unikatowy identyfikator zestawu, aby zostać rozszerzony.  
  
 `ImportToken`  
 Unikatowy identyfikator, pobierane z [importfile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), pliku do zaimportowania.  
  
 `dwFlags`  
 COM + FileDef flagi, takich jak `ffContainsNoMetaData` i `ffWriteable`. `dwFlags` jest przekazywany do [definefile — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Wskaźnik do tokenu, który odbiera identyfikator wynikowy plik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz także

- [IALink — Interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 — Interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink — interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
