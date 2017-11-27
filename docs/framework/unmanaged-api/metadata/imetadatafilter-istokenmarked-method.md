---
title: "IMetaDataFilter::IsTokenMarked — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter.IsTokenMarked
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 832f1e57e55245a84d093a41c627613d5fbe6902
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="069fe-102">IMetaDataFilter::IsTokenMarked — Metoda</span><span class="sxs-lookup"><span data-stu-id="069fe-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="069fe-103">Pobiera wartość wskazującą, czy token określonych metadanych została oznaczona jako przetworzona.</span><span class="sxs-lookup"><span data-stu-id="069fe-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="069fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="069fe-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="069fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="069fe-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="069fe-106">[in] Token do sprawdzenia znaku przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="069fe-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="069fe-107">[out] Wartość, która jest `true` Jeśli `tk` zostało przetworzone; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="069fe-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="069fe-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="069fe-108">Requirements</span></span>  
 <span data-ttu-id="069fe-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="069fe-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="069fe-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="069fe-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="069fe-111">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="069fe-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="069fe-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="069fe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069fe-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="069fe-113">See Also</span></span>  
 [<span data-ttu-id="069fe-114">IMetaDataFilter — interfejs</span><span class="sxs-lookup"><span data-stu-id="069fe-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
