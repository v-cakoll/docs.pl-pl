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
ms.openlocfilehash: c0b6d53ce3be3aed6a577bf6e38a281928499848
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009031"
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
 podczas `mdManifestResource`Token reprezentujący zasób, dla którego mają zostać pobrane właściwości.  
  
 `szName`  
 określoną Nazwa zasobu.  
  
 `cchName`  
 podczas Rozmiar, w postaci szerokich znaków, z `szName` .  
  
 `pchName`  
 określoną Wskaźnik do liczby znaków dwubajtowych faktycznie zwróconych w `szName` .  
  
 `ptkImplementation`  
 określoną Wskaźnik do `mdFile` tokenu lub `mdAssemblyRef` tokenu, który reprezentuje odpowiednio plik lub zestaw, który zawiera zasób.  
  
 `pdwOffset`  
 określoną Wskaźnik do wartości, która określa przesunięcie do początku zasobu w pliku.  
  
 `pdwResourceFlags`  
 określoną Wskaźnik do flag, które opisują metadane zastosowane do zasobu. Wartość flags jest kombinacją co najmniej jednej wartości [CorManifestResourceFlags —](cormanifestresourceflags-enumeration.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyImport — Interfejs](imetadataassemblyimport-interface.md)
