---
title: IMetaDataImport2::EnumGenericParamConstraints — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd5d35cb13bb55fc73e160089cbc1050cb3d5c0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449221"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a>IMetaDataImport2::EnumGenericParamConstraints — Metoda
Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego reprezentowany przez określony token.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, out] Wskaźnik do modułu wyliczającego.  
  
 `tk`  
 [in]   Token, który reprezentuje parametru ogólnego ograniczenia, których mają zostać wyliczone.  
  
 `rGenericParamConstraints`  
 [out] Tablica ograniczenia parametru ogólnego wyliczyć.  
  
 `cMax`  
 [in]   Żądana maksymalna liczba tokenów do umieszczenia w `rGenericParamConstraints`.  
  
 `pcGenericParamConstraints`  
 [out] Wskaźnik do liczby tokenów umieszczone w `rGenericParamConstraints`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` zwrócona pomyślnie.|  
|`S_FALSE`|`phEnum` nie ma żadnych elementów członkowskich. W takim przypadku `pcGenericParameterConstraints` jest równa 0 (zero).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
