---
title: IMetaDataEmit::DefineTypeRefByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82d81be7a9e0843dfe382767de582f93371acb4c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584489"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName — Metoda
Pobiera token metadanych dla typu, który jest zdefiniowany w określonym zakresie, który znajduje się poza bieżącym zakresie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkResolutionScope`  
 [in] Token, określając zakres rozwiązywania. Następujące typy tokenów są prawidłowe:  
  
- `mdModuleRef`, jeśli typ jest zdefiniowany w tym samym zestawie, w którym zdefiniowano element wywołujący.  
  
- `mdAssemblyRef`, jeśli typ jest zdefiniowany w zestawie innym niż ten, w którym zdefiniowano element wywołujący.  
  
- `mdTypeRef`, jeśli typ jest typem zagnieżdżonym.  
  
- `mdModule`, jeśli typ jest zdefiniowany w tym samym module, w którym zdefiniowano element wywołujący.  
  
- Wartość null, jeśli typ jest zdefiniowany jako globalnie.  
  
 `szName`  
 [in] Nazwa typu docelowego w formacie Unicode.  
  
 `ptr`  
 [out] Wskaźnik do `mdTypeRef` token, który jest przypisany do typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
