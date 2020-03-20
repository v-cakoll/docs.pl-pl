---
title: IMetaDataEmit::DefineNestedType — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175814"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType — Metoda
Tworzy podpis metadanych definicji typu, zwraca `mdTypeDef` token dla tego typu i określa, że zdefiniowany `tdEncloser` typ jest członkiem typu, do którego odwołuje się parametr.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [w] Nazwa typu w Unicode.  
  
 `dwTypeDefFlags`  
 [w] `TypeDef` atrybutów. Jest to maska `CorTypeAttr` bitowa wartości.  
  
 `tkExtends`  
 [w] Token klasy podstawowej. Jest to token `mdTypeDef` lub `mdTypeRef` token.  
  
 `rtkImplements`[]  
 [w] Tablica tokenów, które określają interfejsy, które implementuje ta klasa lub interfejs.  
  
 `tdEncloser`  
 [w] Token otaczającego typu. Ostatnim elementem tablicy `mdTokenNil`musi być .  
  
 `ptd`  
 [na zewnątrz] Token `mdTypeDef` przypisany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
