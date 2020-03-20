---
title: IMetaDataEmit2::DefineGenericParam — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 1868d13a9dbb73dbdf64e49c395bdbff02ce89d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177454"
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam — Metoda
Tworzy definicję parametru typu ogólnego i pobiera token do tego parametru typu ogólnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [w] Lub `mdTypeDef` `mdMethodDef` token, który reprezentuje metodę lub konstruktora, dla którego można zdefiniować parametr ogólny.  
  
 `ulParamSeq`  
 [w] Indeks parametru ogólnego.  
  
 `dwParamFlags`  
 [w] Wartość wyliczania [CorGenericParamAttr,](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) która opisuje typ parametru ogólnego.  
  
 `szname`  
 [w] Nazwa parametru.  
  
 `reserved`  
 [w] Ten parametr jest zarezerwowany dla przyszłej rozszerzalności.  
  
 `rtkConstraints`  
 [w] Tablica typu zakończona z zerowym o zerowym zakończeniem. Elementy członkowskie tablicy `mdTypeRef`muszą `mdTypeSpec` być tokenem `mdTypeDef`, lub metadanych.  
  
 `pgp`  
 [na zewnątrz] Token reprezentujący parametr ogólny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
