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
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177712"
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
 [w] Token `mdTypeDef` dla otaczającej klasy lub interfejsu.  
  
 `szName`  
 [w] Nazwa pola w unicode.  
  
 `dwFieldFlags`  
 [w] Atrybuty pola. Jest to maska `CorFieldAttr` bitowa wartości.  
  
 `pvSigBlob`  
 [w] Podpis pola jako obiekt BLOB.  
  
 `cbSigBlob`  
 [w] Liczba bajtów `pvSigBlob`w pliku .  
  
 `dwCPlusTypeFlag`  
 [w] Dla `ELEMENT_TYPE_` *\** wartości stałej. Jest to `CorElementType` wartość. Jeśli nie zdefiniowano stałej wartości `ELEMENT_TYPE_END`dla pola, należy użyć programu .  
  
 `pValue`  
 [w] Stała wartość pola.  
  
 `cchValue`  
 [w] Rozmiar w znakach (Unicode) . `pValue`  
  
 `pmd`  
 [na zewnątrz] Token `mdFieldDef` przypisany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
