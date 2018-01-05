---
title: "IMetaDataEmit::DefineTypeRefByName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeRefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46b9fe83a5beb031d4ac21deb903060e2f788e1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName — Metoda
Pobiera token metadanych dla typu, który jest zdefiniowany w określonym zakresie znajduje się poza bieżącym zakresem.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkResolutionScope`  
 [in] Token określający zakres rozpoznawania. Następujące typy tokenów są prawidłowe:  
  
-   `mdModuleRef`, jeśli typ jest zdefiniowany w tym samym zestawie, w którym jest zdefiniowany element wywołujący.  
  
-   `mdAssemblyRef`, jeśli typ jest zdefiniowany w zestawie innego niż ten, w którym jest zdefiniowany element wywołujący.  
  
-   `mdTypeRef`, jeśli typ jest typem zagnieżdżonym.  
  
-   `mdModule`, jeśli typ jest zdefiniowany w tym samym module, w którym jest zdefiniowany element wywołujący.  
  
-   Wartość null, jeśli typ jest zdefiniowany globalnie.  
  
 `szName`  
 [in] Nazwa typu docelowego w standardzie Unicode.  
  
 `ptr`  
 [out] Wskaźnik do `mdTypeRef` token, który jest przypisany do typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
