---
title: IMetaDataEmit::GetSaveSize — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
ms.openlocfilehash: 125a63638a41707b8eed918253cb1f93abb907eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434335"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="3f515-102">IMetaDataEmit::GetSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f515-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="3f515-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span><span class="sxs-lookup"><span data-stu-id="3f515-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f515-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f515-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f515-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f515-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="3f515-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span><span class="sxs-lookup"><span data-stu-id="3f515-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="3f515-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="3f515-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="3f515-108">cssAccurate returns the exact save size but takes longer to calculate.</span><span class="sxs-lookup"><span data-stu-id="3f515-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="3f515-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span><span class="sxs-lookup"><span data-stu-id="3f515-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="3f515-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span><span class="sxs-lookup"><span data-stu-id="3f515-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="3f515-111">[out] A pointer to the size that is required to save the file.</span><span class="sxs-lookup"><span data-stu-id="3f515-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f515-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f515-112">Remarks</span></span>  
 <span data-ttu-id="3f515-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span><span class="sxs-lookup"><span data-stu-id="3f515-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="3f515-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span><span class="sxs-lookup"><span data-stu-id="3f515-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="3f515-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span><span class="sxs-lookup"><span data-stu-id="3f515-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="3f515-116">Otherwise, no optimizations are performed.</span><span class="sxs-lookup"><span data-stu-id="3f515-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="3f515-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span><span class="sxs-lookup"><span data-stu-id="3f515-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="3f515-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span><span class="sxs-lookup"><span data-stu-id="3f515-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="3f515-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span><span class="sxs-lookup"><span data-stu-id="3f515-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="3f515-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="3f515-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="3f515-121">In this pass, another round of token mapping occurs.</span><span class="sxs-lookup"><span data-stu-id="3f515-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="3f515-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span><span class="sxs-lookup"><span data-stu-id="3f515-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f515-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f515-123">Requirements</span></span>  
 <span data-ttu-id="3f515-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f515-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f515-125">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f515-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f515-126">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f515-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f515-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f515-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f515-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f515-128">See also</span></span>

- [<span data-ttu-id="3f515-129">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="3f515-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3f515-130">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3f515-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
