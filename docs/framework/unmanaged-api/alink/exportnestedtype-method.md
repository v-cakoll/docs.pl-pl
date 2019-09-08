---
title: ExportNestedType — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 570e48788a11045882ef546bf6bc22315c2a02b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777280"
---
# <a name="exportnestedtype-method"></a>ExportNestedType — Metoda
Określa typy zagnieżdżone jako możliwe do eksportowania. [Metoda exporttype](exporttype-method.md) może również eksportować typy zagnieżdżone, ale ta metoda jest szybsza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu do wyeksportowania.  
  
 `FileToken`  
 Token pliku lub zestaw pliku, który definiuje typ, który ma być możliwy do eksportu.  
  
 `TypeToken`  
 Typ token typu, który ma być możliwy do eksportu.  
  
 `ParentType`  
 Token typu nadrzędnego.  
  
 `pszTypename`  
 W pełni kwalifikowana nazwa typu do eksportowania.  
  
 `dwFlags`  
 `ComType`flagi takie jak `tdPublic` lub `tdNested`. Ta wartość może zostać przeniesiona do [metody DefineExportedType —](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Odbiera token dla wyeksportowanego typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
