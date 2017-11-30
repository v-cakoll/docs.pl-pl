---
title: "IMetaDataEmit2::DefineGenericParam — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineGenericParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 737e57b86e74cc7e4668589d16c2e2cb351162bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam — Metoda
Tworzy definicję dla parametru typu ogólnego i pobiera token do tego parametru typu ogólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tk`  
 [in] `mdTypeDef` Lub `mdMethodDef` token, który reprezentuje metody lub konstruktora, który chcesz zdefiniować parametru ogólnego.  
  
 `ulParamSeq`  
 [in] Indeks parametru ogólnego.  
  
 `dwParamFlags`  
 [in] Wartość [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) wyliczenie opisujące typ dla parametru ogólnego.  
  
 `szname`  
 [in] Nazwa parametru.  
  
 `reserved`  
 [in] Ten parametr jest zarezerwowana dla przyszłych rozszerzalności.  
  
 `rtkConstraints`  
 [in] Tablica zakończony zerem ograniczenia typu. Elementy członkowskie tablicy musi być `mdTypeDef`, `mdTypeRef`, lub `mdTypeSpec` token metadanych.  
  
 `pgp`  
 [out] Token, który reprezentuje parametru ogólnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
