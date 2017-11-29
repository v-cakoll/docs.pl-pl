---
title: "IMetaDataEmit::TranslateSigWithScope — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.TranslateSigWithScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5127defc97423283b52b7b5bd8c6b7a31104fbc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope — Metoda
Importuje zestawu do bieżącego zakresu i pobiera nowego podpisu metadanych dla zakresu scalone.  
  
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
 [in] Interfejs dla importu zestawu (w którym jest zdefiniowana podpis).  
  
 `pbHashValue`  
 [in] Obiektu blob generowania skrótu dla zestawu.  
  
 `cbHashValue`  
 [in] Liczba bajtów w `pbHashValue`.  
  
 `import`  
 [in] Interfejs zakresie importu metadanych.  
  
 `pbSigBlob`  
 [in] Podpis do zaimportowania.  
  
 `cbSigBlob`  
 [in] Rozmiar w bajtach z `pbSigBlob`.  
  
 `pAssemEmit`  
 [in] Interfejs dla zestawu eksportu.  
  
 `emit`  
 [in] Interfejs dla zakresu metadanych eksportu.  
  
 `pvTranslatedSig`  
 [out] Bufor do przechowywania obiektów blob przetłumaczonego podpisu.  
  
 `cbTranslatedSigMax`  
 [in] Pojemność, w bajtach z `pvTranslatedSig`.  
  
 `pcbTranslatedSig`  
 [out] Liczba rzeczywista liczba bajtów w przetłumaczonego podpisu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
