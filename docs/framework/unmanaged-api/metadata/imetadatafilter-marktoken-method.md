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
ms.openlocfilehash: 6fdd50f0de014aa68b14303e9e22924b0790fa55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786272"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="65318-102">IMetaDataFilter::MarkToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="65318-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="65318-103">Ustawia wartość wskazującą, przetworzeniu token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="65318-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65318-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65318-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65318-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65318-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="65318-106">[in] Token, aby oznaczyć jako przetworzone.</span><span class="sxs-lookup"><span data-stu-id="65318-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65318-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65318-107">Requirements</span></span>  
 <span data-ttu-id="65318-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65318-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65318-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="65318-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65318-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65318-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65318-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65318-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65318-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65318-112">See also</span></span>

- [<span data-ttu-id="65318-113">IMetaDataFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="65318-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
