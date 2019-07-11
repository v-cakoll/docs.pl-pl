---
title: IMetaDataImport2::GetGenericParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf9f6cc1e568463f2ca9afa38c10f50d0c247013
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755340"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps — Metoda
Pobiera metadane skojarzone z parametru ogólnego, reprezentowane przez określony token.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `gp`  
 [in] Token, który reprezentuje parametr ogólny, dla której ma zostać zwrócone metadanych.  
  
 `pulParamSeq`  
 [out] Numer porządkowy położenie `Type` parametr w Konstruktorze nadrzędnej lub metody.  
  
 `pdwParamFlags`  
 [out] Wartość [corgenericparamattr —](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) wyliczenie opisujące `Type` dla parametru ogólnego.  
  
 `ptOwner`  
 [out] Element TypeDef lub MethodDef token reprezentujący właściciela parametru.  
  
 `reserved`  
 [out] Zarezerwowane dla przyszłej rozszerzalności.  
  
 `wzName`  
 [out] Nazwa parametru ogólnego.  
  
 `cchName`  
 [in] Rozmiar `wzName` buforu.  
  
 `pchName`  
 [out] Rozmiar zwróconego nazwę w znaki dwubajtowe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
