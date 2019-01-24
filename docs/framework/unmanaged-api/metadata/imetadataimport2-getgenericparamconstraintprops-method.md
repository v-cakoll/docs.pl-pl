---
title: IMetaDataImport2::GetGenericParamConstraintProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7761c2f15cd51bff798e1b12c3a5824930b344d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617723"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a>IMetaDataImport2::GetGenericParamConstraintProps — Metoda
Pobiera metadane skojarzone z ograniczenia parametru ogólnego, reprezentowane przez ograniczenie określonego tokenu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `gpc`  
 [in] Token do ograniczenia parametru ogólnego, dla której ma zostać zwrócone metadanych.  
  
 `ptGenericParam`  
 [out] Wskaźnik do tokenu, który reprezentuje parametr generyczny, który jest ograniczony.  
  
 `ptkConstraintType`  
 [out] Wskaźnik do elementu TypeDef, TypeRef lub elementu TypeSpec token, który reprezentuje ograniczenie na `ptGenericParam`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
