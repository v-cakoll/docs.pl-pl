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
ms.openlocfilehash: a0d105679a749b8c87099af871bdb42874d440b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447006"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType — Metoda
Tworzy metadane podpis definicji typu, zwraca `mdTypeDef` token dla tego typu, a następnie określa zdefiniowanego typu elementu członkowskiego typu odwołuje się `tdEncloser` parametru.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [in] Nazwa typu w standardzie Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atrybutów. To jest maską bitów z `CorTypeAttr` wartości.  
  
 `tkExtends`  
 [in] Token klasy podstawowej. Jest to `mdTypeDef` lub `mdTypeRef` tokenu.  
  
 `rtkImplements`[]  
 [in] Tablica określające interfejsów, które implementuje w tej klasy lub interfejsu.  
  
 `tdEncloser`  
 [in] Token typu otaczającego. Musi być ostatnim elementem tablicy `mdTokenNil`.  
  
 `ptd`  
 [out] `mdTypeDef` Token przypisany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
