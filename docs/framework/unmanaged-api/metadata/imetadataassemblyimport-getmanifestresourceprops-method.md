---
title: "IMetaDataAssemblyImport::GetManifestResourceProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29458b0b7afa5a0c0be908915b4fc91c85d28c72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps — Metoda
Pobiera zestaw właściwości zasobu manifestu o sygnaturze określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mdmr`  
 [in] `mdManifestResource` Token reprezentujący zasobu, dla którego można pobrać właściwości.  
  
 `szName`  
 [out] Nazwa zasobu.  
  
 `cchName`  
 [in] Rozmiar w znaki dwubajtowe z `szName`.  
  
 `pchName`  
 [out] Wskaźnik do liczby znaki dwubajtowe faktycznie zwracane w `szName`.  
  
 `ptkImplementation`  
 [out] Wskaźnik do `mdFile` tokenu lub `mdAssemblyRef` token reprezentujący pliku lub zestawu, który zawiera zasób.  
  
 `pdwOffset`  
 [out] Wskaźnik do wartość określa Przesunięcie początku zasobów w pliku.  
  
 `pdwResourceFlags`  
 [out] Wskaźnik do flagi opisujące metadanych dla zasobu. Wartość flagi składa się z co najmniej jeden [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
