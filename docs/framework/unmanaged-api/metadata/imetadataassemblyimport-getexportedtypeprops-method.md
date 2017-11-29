---
title: "IMetaDataAssemblyImport::GetExportedTypeProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e142d0c77493ac1e9ab2bf485d8e111af4fb3ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps — Metoda
Pobiera zestaw właściwości wyeksportowanego typu podpisem określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mdct`  
 [in] `mdExportedType` Token metadanych, który reprezentuje wyeksportowanego typu.  
  
 `szName`  
 [out] Nazwa wyeksportowanego typu.  
  
 `cchName`  
 [in] Rozmiar w znaki dwubajtowe z `szName`.  
  
 `pchName`  
 [out] Liczba faktycznie zwracane w znaki dwubajtowe`szName`  
  
 `ptkImplementation`  
 [out] `mdFile`, `mdAssemblyRef`, Lub `mdExportedType` token metadanych, który zawiera lub udziela dostępu do właściwości wyeksportowanego typu.  
  
 `ptkTypeDef`  
 [out] Wskaźnik do `mdTypeDef` token, który reprezentuje typ pliku.  
  
 `pdwExportedTypeFlags`  
 [out] Wskaźnik do flag, które opisują metadanych stosowane do wyeksportowanego typu. Wartość flagi może być co najmniej jeden [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
