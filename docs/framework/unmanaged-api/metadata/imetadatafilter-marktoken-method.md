---
title: IMetaDataFilter::MarkToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97f184bae4628f2aa357644188594396468671ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444155"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="6e08b-102">IMetaDataFilter::MarkToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="6e08b-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="6e08b-103">Ustawia wartość wskazującą przetworzeniu token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="6e08b-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e08b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e08b-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e08b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e08b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6e08b-106">[in] Token do oznaczania w trakcie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="6e08b-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e08b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e08b-107">Requirements</span></span>  
 <span data-ttu-id="6e08b-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e08b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e08b-109">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6e08b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e08b-110">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e08b-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e08b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e08b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e08b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e08b-112">See Also</span></span>  
 [<span data-ttu-id="6e08b-113">IMetaDataFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="6e08b-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
