---
title: "IHostFilter::MarkToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ca342e04f554d070546c6c6d82d5ad56a4dad8cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="13364-102">IHostFilter::MarkToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="13364-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="13364-103">Wskazuje token określonych metadanych zostaną przetworzone.</span><span class="sxs-lookup"><span data-stu-id="13364-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13364-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13364-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13364-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13364-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="13364-106">[in] Token metadanych do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="13364-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13364-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13364-107">Remarks</span></span>  
 <span data-ttu-id="13364-108">Zwykle ma token do przetworzenia, jeśli znajduje się w zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="13364-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="13364-109">`MarkToken` Metody jest przekazywany do aparatu metadanych za pośrednictwem [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="13364-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13364-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13364-110">Requirements</span></span>  
 <span data-ttu-id="13364-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13364-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13364-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13364-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13364-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13364-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13364-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13364-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13364-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13364-115">See Also</span></span>  
 [<span data-ttu-id="13364-116">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="13364-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="13364-117">IHostFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="13364-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
