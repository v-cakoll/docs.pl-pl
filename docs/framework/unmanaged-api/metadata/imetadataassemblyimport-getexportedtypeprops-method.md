---
title: IMetaDataAssemblyImport::GetExportedTypeProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 944941c2356cae93ecc85f1714b4b29aefcb50ad
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008407"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps — Metoda
Pobiera zestaw właściwości wyeksportowanego typu z określonym podpisem metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `mdct`  
 podczas `mdExportedType`Token metadanych reprezentujący wyeksportowany typ.  
  
 `szName`  
 określoną Nazwa wyeksportowanego typu.  
  
 `cchName`  
 podczas Rozmiar, w postaci znaków dwubajtowych, z `szName` .  
  
 `pchName`  
 określoną Liczba znaków dwubajtowych rzeczywiście zwróconych w`szName`  
  
 `ptkImplementation`  
 określoną `mdFile` `mdAssemblyRef` Lub `mdExportedType` token metadanych, który zawiera lub zezwala na dostęp do właściwości wyeksportowanego typu.  
  
 `ptkTypeDef`  
 określoną Wskaźnik do `mdTypeDef` tokenu, który reprezentuje typ w pliku.  
  
 `pdwExportedTypeFlags`  
 określoną Wskaźnik do flag opisujących metadane zastosowane do wyeksportowanego typu. Wartość flag może być jedną lub większą liczbą wartości [CorTypeAttr —](cortypeattr-enumeration.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyImport — Interfejs](imetadataassemblyimport-interface.md)
