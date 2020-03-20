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
ms.openlocfilehash: 2662af41fbd2cdc3ce8a6df1e036dfc5b22ff6a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175554"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="2a108-102">IMetaDataEmit::TranslateSigWithScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a108-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="2a108-103">Importuje zestaw do bieżącego zakresu i pobiera nowy podpis metadanych dla scalonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="2a108-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a108-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a108-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2a108-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a108-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="2a108-106">[w] Interfejs zestawu importu (w którym zdefiniowano podpis).</span><span class="sxs-lookup"><span data-stu-id="2a108-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="2a108-107">[w] Obiekt blob skrótu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="2a108-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="2a108-108">[w] Liczba bajtów `pbHashValue`w pliku .</span><span class="sxs-lookup"><span data-stu-id="2a108-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="2a108-109">[w] Interfejs dla zakresu metadanych importu.</span><span class="sxs-lookup"><span data-stu-id="2a108-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="2a108-110">[w] Podpis do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="2a108-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="2a108-111">[w] Rozmiar w bajtach `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="2a108-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="2a108-112">[w] Interfejs do zestawu eksportu.</span><span class="sxs-lookup"><span data-stu-id="2a108-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="2a108-113">[w] Interfejs do eksportu zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="2a108-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="2a108-114">[na zewnątrz] Bufor do przechowywania przetłumaczonego obiektu blob podpisu.</span><span class="sxs-lookup"><span data-stu-id="2a108-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="2a108-115">[w] Pojemność w bajtach `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="2a108-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="2a108-116">[na zewnątrz] Liczba bajtów rzeczywistych w przetłumaczonym podpisie.</span><span class="sxs-lookup"><span data-stu-id="2a108-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a108-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a108-117">Requirements</span></span>  
 <span data-ttu-id="2a108-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a108-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a108-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="2a108-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a108-120">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a108-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a108-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a108-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a108-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a108-122">See also</span></span>

- [<span data-ttu-id="2a108-123">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2a108-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="2a108-124">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2a108-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="2a108-125">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2a108-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2a108-126">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a108-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="2a108-127">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2a108-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
