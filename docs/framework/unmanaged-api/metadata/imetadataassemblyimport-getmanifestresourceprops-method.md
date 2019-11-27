---
title: IMetaDataAssemblyImport::GetManifestResourceProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: c1792ed0f15f8cfb62567593c9694453650f0bb9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436319"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps — Metoda
Pobiera zestaw właściwości zasobu manifestu z określonym podpisem metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `mdmr`  
 podczas Token `mdManifestResource` reprezentujący zasób, dla którego mają zostać pobrane właściwości.  
  
 `szName`  
 określoną Nazwa zasobu.  
  
 `cchName`  
 podczas Rozmiar, w postaci szerokich znaków, `szName`.  
  
 `pchName`  
 określoną Wskaźnik do liczby znaków dwubajtowych faktycznie zwróconych w `szName`.  
  
 `ptkImplementation`  
 określoną Wskaźnik do tokenu `mdFile` lub token `mdAssemblyRef`, który reprezentuje odpowiednio plik lub zestaw, który zawiera zasób.  
  
 `pdwOffset`  
 określoną Wskaźnik do wartości, która określa przesunięcie do początku zasobu w pliku.  
  
 `pdwResourceFlags`  
 określoną Wskaźnik do flag, które opisują metadane zastosowane do zasobu. Wartość flags jest kombinacją co najmniej jednej wartości [CorManifestResourceFlags —](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
