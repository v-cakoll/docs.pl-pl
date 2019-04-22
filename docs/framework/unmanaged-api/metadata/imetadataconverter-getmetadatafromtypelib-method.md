---
title: IMetaDataConverter::GetMetaDataFromTypeLib — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cdc1b0de9795a000ee680df880c73acc4f711db2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145330"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a>IMetaDataConverter::GetMetaDataFromTypeLib — Metoda
Pobiera wskaźnik interfejsu do [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wystąpienia, która reprezentuje podpis metadanych biblioteki typów, reprezentowane przez określony `ITypeLib` wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pITL`  
 [in] Wskaźnik do `ITypeLib` obiekt, który reprezentuje biblioteki typów.  
  
 `ppMDI`  
 [out] Wskaźnik do lokalizacji, która otrzymuje adres `IMetaDataImport` wystąpienia, która reprezentuje podpis metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
