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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b54ceb099df15855b6b30b8c28d7d8917a9c71eb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184952"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField — Metoda
Tworzy definicję dla pola przy użyciu podpisu określonych metadanych, a następnie pobiera token do tej definicji pola.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [in] `mdTypeDef` Tokenu dla otaczającej klasy lub interfejsu.  
  
 `szName`  
 [in] Nazwa pola w formacie Unicode.  
  
 `dwFieldFlags`  
 [in] Atrybuty pól. Jest to z `CorFieldAttr` wartości.  
  
 `pvSigBlob`  
 [in] Podpis pola jako obiekt BLOB.  
  
 `cbSigBlob`  
 [in] Liczba bajtów w `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** Wartości stałej. Jest to `CorElementType` wartość. Jeśli nie definiuje stałą wartość dla pola, użyj `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] Stała wartość dla pola.  
  
 `cchValue`  
 [in] Rozmiar w znakach (Unicode) `pValue`.  
  
 `pmd`  
 [out] `mdFieldDef` Token przypisany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
