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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da52d540266e2c5f9bfc7f1a83d2683fa765914b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478756"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType — Metoda
Tworzy podpisu metadanych w definicji typu, zwraca `mdTypeDef` tokenu dla tego typu i określa, że typ zdefiniowany jest elementem członkowskim typu odwołuje się `tdEncloser` parametru.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Nazwa typu w formacie Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atrybutów. Jest to z `CorTypeAttr` wartości.  
  
 `tkExtends`  
 [in] Token klasy bazowej. Jest to `mdTypeDef` lub `mdTypeRef` tokenu.  
  
 `rtkImplements`[]  
 [in] Tablica tokenów, które określają interfejsy, które implementuje tej klasy lub interfejsu.  
  
 `tdEncloser`  
 [in] Token typ otaczający. Ostatni element tablicy muszą być `mdTokenNil`.  
  
 `ptd`  
 [out] `mdTypeDef` Token przypisany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
