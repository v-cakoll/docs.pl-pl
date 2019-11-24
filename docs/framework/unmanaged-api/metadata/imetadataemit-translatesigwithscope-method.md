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
ms.openlocfilehash: cea84f47a5289df4bc9c50381e18d7077b3b8dad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440476"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="c41c9-102">IMetaDataEmit::TranslateSigWithScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="c41c9-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="c41c9-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span><span class="sxs-lookup"><span data-stu-id="c41c9-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c41c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c41c9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c41c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c41c9-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="c41c9-106">[in] The interface for import assembly (where the signature is defined).</span><span class="sxs-lookup"><span data-stu-id="c41c9-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c41c9-107">[in] The hash blob for the assembly.</span><span class="sxs-lookup"><span data-stu-id="c41c9-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c41c9-108">[in] The count of bytes in `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="c41c9-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="c41c9-109">[in] The interface for import metadata scope.</span><span class="sxs-lookup"><span data-stu-id="c41c9-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="c41c9-110">[in] The signature to be imported.</span><span class="sxs-lookup"><span data-stu-id="c41c9-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c41c9-111">[in] The size, in bytes, of `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="c41c9-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="c41c9-112">[in] The interface for export assembly.</span><span class="sxs-lookup"><span data-stu-id="c41c9-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="c41c9-113">[in] The interface for export metadata scope.</span><span class="sxs-lookup"><span data-stu-id="c41c9-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="c41c9-114">[out] The buffer to hold the translated signature blob.</span><span class="sxs-lookup"><span data-stu-id="c41c9-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="c41c9-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="c41c9-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="c41c9-116">[out] The number of actual bytes in the translated signature.</span><span class="sxs-lookup"><span data-stu-id="c41c9-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c41c9-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c41c9-117">Requirements</span></span>  
 <span data-ttu-id="c41c9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c41c9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c41c9-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c41c9-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c41c9-120">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c41c9-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c41c9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c41c9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c41c9-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c41c9-122">See also</span></span>

- [<span data-ttu-id="c41c9-123">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="c41c9-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="c41c9-124">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="c41c9-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="c41c9-125">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="c41c9-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c41c9-126">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c41c9-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="c41c9-127">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="c41c9-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
