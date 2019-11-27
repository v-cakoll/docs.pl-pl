---
title: IMetaDataEmit::DefineField — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432549"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField — Metoda
Tworzy definicję dla pola z określonym podpisem metadanych i pobiera token do tej definicji pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 podczas Token `mdTypeDef` dotyczący otaczającej klasy lub interfejsu.  
  
 `szName`  
 podczas Nazwa pola w formacie Unicode.  
  
 `dwFieldFlags`  
 podczas Atrybuty pola. To jest maska bitów wartości `CorFieldAttr`.  
  
 `pvSigBlob`  
 podczas Podpis pola jako obiekt BLOB.  
  
 `cbSigBlob`  
 podczas Liczba bajtów w `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 podczas `ELEMENT_TYPE_` *\** wartości stałej. To jest wartość `CorElementType`. Jeśli nie zdefiniowano wartości stałej dla pola, użyj `ELEMENT_TYPE_END`.  
  
 `pValue`  
 podczas Stała wartość pola.  
  
 `cchValue`  
 podczas Znaki w formacie (Unicode) `pValue`.  
  
 `pmd`  
 określoną Przypisany token `mdFieldDef`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
