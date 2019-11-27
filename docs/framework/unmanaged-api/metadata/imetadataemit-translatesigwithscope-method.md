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
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="6815d-102">IMetaDataEmit::TranslateSigWithScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="6815d-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="6815d-103">Importuje zestaw do bieżącego zakresu i pobiera nowy podpis metadanych dla scalonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="6815d-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6815d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6815d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6815d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6815d-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="6815d-106">podczas Interfejs dla zestawu importu (gdzie sygnatura jest zdefiniowana).</span><span class="sxs-lookup"><span data-stu-id="6815d-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="6815d-107">podczas Obiekt BLOB mieszania dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="6815d-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="6815d-108">podczas Liczba bajtów w `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="6815d-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="6815d-109">podczas Interfejs dla zakresu metadanych importu.</span><span class="sxs-lookup"><span data-stu-id="6815d-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="6815d-110">podczas Podpis do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="6815d-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6815d-111">podczas Rozmiar w bajtach `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="6815d-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="6815d-112">podczas Interfejs do eksportowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="6815d-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="6815d-113">podczas Interfejs do eksportowania zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="6815d-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="6815d-114">określoną Bufor do przechowywania przetłumaczonego obiektu BLOB sygnatury.</span><span class="sxs-lookup"><span data-stu-id="6815d-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="6815d-115">podczas Pojemność, w bajtach, `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="6815d-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="6815d-116">określoną Liczba rzeczywistych bajtów w przetłumaczonym podpisie.</span><span class="sxs-lookup"><span data-stu-id="6815d-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6815d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6815d-117">Requirements</span></span>  
 <span data-ttu-id="6815d-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6815d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6815d-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6815d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6815d-120">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6815d-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6815d-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6815d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6815d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6815d-122">See also</span></span>

- [<span data-ttu-id="6815d-123">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="6815d-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="6815d-124">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6815d-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="6815d-125">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="6815d-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6815d-126">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6815d-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="6815d-127">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6815d-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
