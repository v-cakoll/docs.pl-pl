---
title: "ExportTypeForwarder — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3fe418b1f8a5d5a6d3c2d36184ca76d5ef9989bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="exporttypeforwarder-method"></a>ExportTypeForwarder — Metoda
Dodaje usługę przesyłania dalej dla typu tabeli typu danego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkAssemblyRef`  
 Odwołanie do zestawu, do którego odwołuje się typ usługi przesyłania dalej.  
  
 `pszTypename`  
 Pełni kwalifikowana nazwa typu do wyeksportowania.  
  
 `dwFlags`  
 `ComType`flagi, takich jak `tdPublic` lub `tdNested`. Ta wartość może być przekazana do [DefineExportedType — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Odbiera token wyeksportowanego typu. Jest to konieczne tylko w przypadku emitowanie zagnieżdżone typy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz też  
 [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
