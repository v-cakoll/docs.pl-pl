---
title: ExportType — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
ms.openlocfilehash: 84c41e467c57afd2562e7aa8dd72ce4796249667
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438568"
---
# <a name="exporttype-method"></a>ExportType — Metoda
Określa, że typ jest eksportowalny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu do wyeksportowania.  
  
 `FileToken`  
 Token pliku lub identyfikator zestawu pliku, który definiuje typ możliwy do eksportu.  
  
 `TypeToken`  
 Token typu, który ma być możliwy do eksportu.  
  
 `pszTypename`  
 W pełni kwalifikowana nazwa typu, która ma zostać wyeksportowana.  
  
 `dwFlags`  
 `ComType` flagi, takie jak `tdPublic` lub `tdNested`. Ten parametr może być przesłany do [metody DefineExportedType —](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
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
