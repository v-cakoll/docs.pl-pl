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
ms.openlocfilehash: ccc4843864f375c167acdb12575c282dbe3a49e1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004819"
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
 podczas `mdTypeDef`Token dla otaczającej klasy lub interfejsu.  
  
 `szName`  
 podczas Nazwa pola w formacie Unicode.  
  
 `dwFieldFlags`  
 podczas Atrybuty pola. To jest maska bitów `CorFieldAttr` wartości.  
  
 `pvSigBlob`  
 podczas Podpis pola jako obiekt BLOB.  
  
 `cbSigBlob`  
 podczas Liczba bajtów w `pvSigBlob` .  
  
 `dwCPlusTypeFlag`  
 podczas `ELEMENT_TYPE_` *\** Wartość stałej. To jest `CorElementType` wartość. Jeśli nie definiuje wartości stałej dla pola, użyj `ELEMENT_TYPE_END` .  
  
 `pValue`  
 podczas Stała wartość pola.  
  
 `cchValue`  
 podczas Znaki w formacie (Unicode) `pValue` .  
  
 `pmd`  
 określoną `mdFieldDef`Przypisany token.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
