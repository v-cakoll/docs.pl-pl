---
title: IHostFilter::MarkToken — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4a1761f088732cf19d55f42d66288bb281885f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589454"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="8bccb-102">IHostFilter::MarkToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="8bccb-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="8bccb-103">Wskazuje token określonych metadanych zostaną przetworzone.</span><span class="sxs-lookup"><span data-stu-id="8bccb-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bccb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bccb-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8bccb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bccb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="8bccb-106">[in] Token metadanych, które mają być przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="8bccb-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bccb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8bccb-107">Remarks</span></span>  
 <span data-ttu-id="8bccb-108">Zazwyczaj chcesz tokenu służącego do ich przetworzyć, jeśli znajduje się w zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8bccb-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="8bccb-109">`MarkToken` Metody jest przekazywany do aparatu metadanych za pośrednictwem [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8bccb-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bccb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bccb-110">Requirements</span></span>  
 <span data-ttu-id="8bccb-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bccb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bccb-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8bccb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bccb-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8bccb-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bccb-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bccb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bccb-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bccb-115">See also</span></span>
- [<span data-ttu-id="8bccb-116">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="8bccb-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="8bccb-117">IHostFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="8bccb-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
