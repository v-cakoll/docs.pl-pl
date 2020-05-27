---
title: IMetaDataAssemblyImport::GetFileProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: 78c192f10f629a0c1316ae7af7fc774819f4de8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007484"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps — Metoda
Pobiera właściwości pliku z określonym podpisem metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mdf`  
 podczas `mdFile`Token metadanych reprezentujący plik, dla którego mają zostać pobrane właściwości.  
  
 `szName`  
 określoną Prosta nazwa pliku.  
  
 `cchName`  
 podczas Rozmiar, w postaci szerokich znaków, z `szName` .  
  
 `pchName`  
 określoną Liczba znaków dwubajtowych, które są w rzeczywistości zwracane `szName` .  
  
 `ppbHashValue`  
 określoną Wskaźnik do wartości skrótu. Jest to skrót, przy użyciu algorytmu SHA-1 pliku.  
  
 `pcbHashValue`  
 określoną Liczba znaków dwubajtowych w zwracanej wartości skrótu.  
  
 `pdwFileFlags`  
 określoną Wskaźnik do flag, które opisują metadane zastosowane do pliku. Wartość flags jest kombinacją co najmniej jednej wartości [CorFileFlags —](corfileflags-enumeration.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyImport — Interfejs](imetadataassemblyimport-interface.md)
