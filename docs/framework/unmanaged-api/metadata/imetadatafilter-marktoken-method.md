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
ms.openlocfilehash: fd0c1edf5eb01c3cb94633b5185ef5b21bd9716e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557863"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="4de02-102">IMetaDataFilter::MarkToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="4de02-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="4de02-103">Ustawia wartość wskazującą, przetworzeniu token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="4de02-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4de02-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4de02-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4de02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4de02-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="4de02-106">[in] Token, aby oznaczyć jako przetworzone.</span><span class="sxs-lookup"><span data-stu-id="4de02-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4de02-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4de02-107">Requirements</span></span>  
 <span data-ttu-id="4de02-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4de02-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4de02-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4de02-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4de02-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4de02-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4de02-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4de02-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de02-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4de02-112">See also</span></span>
- [<span data-ttu-id="4de02-113">IMetaDataFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="4de02-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
