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
ms.openlocfilehash: 4dfb31a2fad8a07b3821ac85bbb43b25693f11d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404109"
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder — Metoda
Dodaje typ usługi przesyłania dalej dla typu zagnieżdżonego typu tabeli danego zestawu.  
  
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
 Identyfikator zestawu eksportu.  
  
 `FileToken`  
 Identyfikator tokenu lub zestawu pliku, który definiuje typ pliku.  
  
 `TypeToken`  
 Token dla typu.  
  
 `ParentType`  
 Token typu nadrzędnego.  
  
 `pszTypename`  
 Pełni kwalifikowana nazwa typu do wyeksportowania.  
  
 `dwFlags`  
 `ComType` flagi, takich jak `tdPublic` lub `tdNested`.  
  
 `pType`  
 Odbiera token typu eksportu. Jest to konieczne tylko w przypadku emitowanie zagnieżdżone typy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz też  
 [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
