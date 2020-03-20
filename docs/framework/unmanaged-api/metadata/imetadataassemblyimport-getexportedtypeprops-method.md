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
ms.openlocfilehash: 15b58e01d4ce99f19f510c760819471b84380b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177756"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps — Metoda
Pobiera zestaw właściwości eksportowanego typu z określonym podpisem metadanych.  
  
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
 [w] Token `mdExportedType` metadanych reprezentujący eksportowany typ.  
  
 `szName`  
 [na zewnątrz] Nazwa wyeksportowanego typu.  
  
 `cchName`  
 [w] Rozmiar, w szerokich `szName`znaków, z .  
  
 `pchName`  
 [na zewnątrz] Liczba szerokich znaków rzeczywiście zwróconych w`szName`  
  
 `ptkImplementation`  
 [na zewnątrz] Token `mdFile` `mdAssemblyRef`, `mdExportedType` lub metadanych, który zawiera lub umożliwia dostęp do właściwości eksportowanego typu.  
  
 `ptkTypeDef`  
 [na zewnątrz] Wskaźnik do `mdTypeDef` tokenu, który reprezentuje typ w pliku.  
  
 `pdwExportedTypeFlags`  
 [na zewnątrz] Wskaźnik do flag, które opisują metadane zastosowane do eksportowanego typu. Wartość flag może być jedną lub kilkoma [wartościami CorTypeAttr.](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
