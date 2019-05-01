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
ms.openlocfilehash: 55a765fe3942cbf71a8460187e829dc7f3ca877e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049859"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps — Metoda
Pobiera metadane skojarzone z parametru ogólnego, reprezentowane przez określony token.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
