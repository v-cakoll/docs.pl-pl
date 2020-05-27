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
ms.openlocfilehash: 2b24c2ca6907dfdb63ad934ec30557c246db174c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004359"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType — Metoda
Tworzy sygnaturę metadanych definicji typu, zwraca `mdTypeDef` token dla tego typu i określa, że zdefiniowany typ jest składową typu, do którego odwołuje się `tdEncloser` parametr.  
  
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
 podczas Nazwa typu w formacie Unicode.  
  
 `dwTypeDefFlags`  
 [w] `TypeDef` Attributes. To jest maska bitów `CorTypeAttr` wartości.  
  
 `tkExtends`  
 podczas Token klasy bazowej. Jest to albo `mdTypeDef` `mdTypeRef` token.  
  
 `rtkImplements`[]  
 podczas Tablica tokenów, które określają interfejsy, które implementuje Ta klasa lub interfejs.  
  
 `tdEncloser`  
 podczas Token typu otaczającego. Ostatni element tablicy musi być `mdTokenNil` .  
  
 `ptd`  
 określoną `mdTypeDef`Przypisany token.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
