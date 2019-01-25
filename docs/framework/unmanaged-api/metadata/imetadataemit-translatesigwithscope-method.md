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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e03572a4eaa0251866e8bfc6ae2d01d955d7b8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516190"
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope — Metoda
Importuje zestawu do bieżącego zakresu, a następnie pobiera nowa sygnatura metadanych dla zakresu scalone.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `pAssemImport`  
 [in] Interfejs dla importu zestawu (gdzie definiuje się podpis).  
  
 `pbHashValue`  
 [in] Obiekt blob wyznaczania wartości skrótu dla zestawu.  
  
 `cbHashValue`  
 [in] Liczba bajtów w `pbHashValue`.  
  
 `import`  
 [in] Interfejs dla zakresu metadanych importu.  
  
 `pbSigBlob`  
 [in] Podpis, który ma zostać zaimportowany.  
  
 `cbSigBlob`  
 [in] Rozmiar w bajtach z `pbSigBlob`.  
  
 `pAssemEmit`  
 [in] Interfejs dla zestawu eksportu.  
  
 `emit`  
 [in] Interfejs dla zakresu metadanych eksportu.  
  
 `pvTranslatedSig`  
 [out] Bufor do przechowywania obiektów blob przetłumaczone podpisu.  
  
 `cbTranslatedSigMax`  
 [in] Pojemność, w bajtach, z `pvTranslatedSig`.  
  
 `pcbTranslatedSig`  
 [out] Liczba rzeczywista liczba bajtów w podpisie tłumaczenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
