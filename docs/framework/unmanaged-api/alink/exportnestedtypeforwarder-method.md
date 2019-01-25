---
title: ExportNestedTypeForwarder — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25b7a708bb2f16433d9de9b5fc1c178cb48874a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658471"
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder — Metoda
Dodaje typ usługi przesyłania dalej dla typu zagnieżdżonego do tabeli typu danego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu, aby wyeksportować z.  
  
 `FileToken`  
 Identyfikator tokenu lub zestawu w pliku, który definiuje typ pliku.  
  
 `TypeToken`  
 Token dla typu.  
  
 `ParentType`  
 Token typie elementu nadrzędnego.  
  
 `pszTypename`  
 W pełni kwalifikowana nazwa typu do wyeksportowania.  
  
 `dwFlags`  
 `ComType` flagi, takich jak `tdPublic` lub `tdNested`.  
  
 `pType`  
 Odbiera token typu eksportu. Jest to niezbędne tylko w przypadku emitowania zagnieżdżone typy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz także
- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
