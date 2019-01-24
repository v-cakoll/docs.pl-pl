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
ms.openlocfilehash: e7a51d1ddf7a5a65ce8713161c53c1c54a5d8861
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617697"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a>IMetaDataImport2::EnumGenericParamConstraints — Metoda
Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego, reprezentowane przez określony token.  
  
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
 [out w] Wskaźnik do modułu wyliczającego.  
  
 `tk`  
 [in]   Token, który reprezentuje parametr ogólny, z którego ograniczenia są do wyliczenia.  
  
 `rGenericParamConstraints`  
 [out] Tablica ograniczenia parametru ogólnego do wyliczenia.  
  
 `cMax`  
 [in]   Żądana maksymalna liczba tokenów do umieszczenia w `rGenericParamConstraints`.  
  
 `pcGenericParamConstraints`  
 [out] Wskaźnik do liczby tokenów umieszczone w `rGenericParamConstraints`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` pomyślnie zwrócił.|  
|`S_FALSE`|`phEnum` nie ma żadnych elementów członkowskich. W tym przypadku `pcGenericParameterConstraints` jest ustawiona na 0 (zero).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
