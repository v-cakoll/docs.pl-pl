---
title: IMetaDataEmit::TranslateSigWithScope — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: 7ef6dbc46806febc6fba89b39a8b894377225c23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003987"
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope — Metoda
Importuje zestaw do bieżącego zakresu i pobiera nowy podpis metadanych dla scalonego zakresu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT TranslateSigWithScope (
    [in]  IMetaDataAssemblyImport   *pAssemImport,
    [in]  const void                *pbHashValue,
    [in]  ULONG                     cbHashValue,
    [in]  IMetaDataImport           *import,
    [in]  PCCOR_SIGNATURE           pbSigBlob,
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,
    [in]  IMetaDataEmit             *emit,
    [out] PCOR_SIGNATURE            pvTranslatedSig,
    [in]  ULONG                     cbTranslatedSigMax,
    [out] ULONG                     *pcbTranslatedSig
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAssemImport`  
 podczas Interfejs dla zestawu importu (gdzie sygnatura jest zdefiniowana).  
  
 `pbHashValue`  
 podczas Obiekt BLOB mieszania dla zestawu.  
  
 `cbHashValue`  
 podczas Liczba bajtów w `pbHashValue` .  
  
 `import`  
 podczas Interfejs dla zakresu metadanych importu.  
  
 `pbSigBlob`  
 podczas Podpis do zaimportowania.  
  
 `cbSigBlob`  
 podczas Rozmiar, w bajtach, z `pbSigBlob` .  
  
 `pAssemEmit`  
 podczas Interfejs do eksportowania zestawu.  
  
 `emit`  
 podczas Interfejs do eksportowania zakresu metadanych.  
  
 `pvTranslatedSig`  
 określoną Bufor do przechowywania przetłumaczonego obiektu BLOB sygnatury.  
  
 `cbTranslatedSigMax`  
 podczas Pojemność, w bajtach, z `pvTranslatedSig` .  
  
 `pcbTranslatedSig`  
 określoną Liczba rzeczywistych bajtów w przetłumaczonym podpisie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport — Interfejs](imetadataassemblyimport-interface.md)
- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
