---
title: "IMetaDataEmit::GetTokenFromTypeSpec — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetTokenFromTypeSpec
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6acb9d340aa1dc8df5d0b9dc3b0c0dd9c159257e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="73c9b-102">IMetaDataEmit::GetTokenFromTypeSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="73c9b-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="73c9b-103">Pobiera token metadanych dla typu o sygnaturze określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="73c9b-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73c9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73c9b-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73c9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73c9b-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="73c9b-106">[in] Podpis jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="73c9b-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="73c9b-107">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="73c9b-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="73c9b-108">[out] `mdTypeSpec` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="73c9b-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73c9b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73c9b-109">Requirements</span></span>  
 <span data-ttu-id="73c9b-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73c9b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73c9b-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="73c9b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73c9b-112">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73c9b-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73c9b-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73c9b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c9b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73c9b-114">See Also</span></span>  
 [<span data-ttu-id="73c9b-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="73c9b-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="73c9b-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="73c9b-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
