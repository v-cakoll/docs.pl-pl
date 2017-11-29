---
title: "IMetaDataAssemblyImport::FindManifestResourceByName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindManifestResourceByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492f8a50c421df56d1b2f79d15d86ef3251b401e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a>IMetaDataAssemblyImport::FindManifestResourceByName — Metoda
Pobiera wskaźnik do zasobu manifestu o określonej nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [in] Nazwa zasobu.  
  
 `ptkManifestResource`  
 [out] Tablica używany do przechowywania `mdManifestResource` tokenów metadanych, z których każdy reprezentuje zasobu manifestu.  
  
## <a name="remarks"></a>Uwagi  
 `FindManifestResourceByName` Metoda używa standardowych zasad stosowanych przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [Jak lokalizuje zestawów przez środowisko uruchomieniowe](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
