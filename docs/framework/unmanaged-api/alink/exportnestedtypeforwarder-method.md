---
title: "ExportNestedTypeForwarder — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportNestedTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedTypeForwarder
helpviewer_keywords: ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eee41e9f71d600a74cc9f74b538ad9e215f0d905
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 `ComType`flagi, takich jak `tdPublic` lub `tdNested`.  
  
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
