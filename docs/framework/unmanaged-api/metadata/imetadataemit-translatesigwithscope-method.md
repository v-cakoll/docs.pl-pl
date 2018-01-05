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
ms.workload: dotnet
ms.openlocfilehash: ceb6a8bfbee5823e7080d8c98647da93a10a5b79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="cb3b5-102">IMetaDataEmit::TranslateSigWithScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb3b5-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="cb3b5-103">Importuje zestawu do bieżącego zakresu i pobiera nowego podpisu metadanych dla zakresu scalone.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb3b5-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="cb3b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb3b5-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="cb3b5-106">[in] Interfejs dla importu zestawu (w którym jest zdefiniowana podpis).</span><span class="sxs-lookup"><span data-stu-id="cb3b5-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="cb3b5-107">[in] Obiektu blob generowania skrótu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="cb3b5-108">[in] Liczba bajtów w `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="cb3b5-109">[in] Interfejs zakresie importu metadanych.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="cb3b5-110">[in] Podpis do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="cb3b5-111">[in] Rozmiar w bajtach z `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="cb3b5-112">[in] Interfejs dla zestawu eksportu.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="cb3b5-113">[in] Interfejs dla zakresu metadanych eksportu.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="cb3b5-114">[out] Bufor do przechowywania obiektów blob przetłumaczonego podpisu.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="cb3b5-115">[in] Pojemność, w bajtach z `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="cb3b5-116">[out] Liczba rzeczywista liczba bajtów w przetłumaczonego podpisu.</span><span class="sxs-lookup"><span data-stu-id="cb3b5-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb3b5-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb3b5-117">Requirements</span></span>  
 <span data-ttu-id="cb3b5-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb3b5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb3b5-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb3b5-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb3b5-120">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb3b5-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb3b5-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb3b5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3b5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb3b5-122">See Also</span></span>  
 [<span data-ttu-id="cb3b5-123">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb3b5-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="cb3b5-124">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb3b5-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="cb3b5-125">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb3b5-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="cb3b5-126">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb3b5-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="cb3b5-127">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb3b5-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
