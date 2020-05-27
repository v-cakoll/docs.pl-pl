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
ms.openlocfilehash: ef6f7a1a6e86b45acce91792385bc3761dfb4c39
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009083"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a>IMetaDataAssemblyImport::FindManifestResourceByName — Metoda
Pobiera wskaźnik do zasobu manifestu o podanej nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 podczas Nazwa zasobu.  
  
 `ptkManifestResource`  
 określoną Tablica służąca do przechowywania `mdManifestResource` tokenów metadanych, z których każdy reprezentuje zasób manifestu.  
  
## <a name="remarks"></a>Uwagi  
 `FindManifestResourceByName`Metoda używa standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyImport — Interfejs](imetadataassemblyimport-interface.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../deployment/how-the-runtime-locates-assemblies.md)
