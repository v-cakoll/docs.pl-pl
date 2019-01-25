---
title: IMetaDataAssemblyImport::FindManifestResourceByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b05c9a75bf870dd3b2316d2df7c50932b26894f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702746"
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
 [out] Tablica do przechowywania `mdManifestResource` tokeny metadanych, z których każdy reprezentuje zasobu manifestu.  
  
## <a name="remarks"></a>Uwagi  
 `FindManifestResourceByName` Metoda wykorzystuje standardowe reguły stosowane przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
