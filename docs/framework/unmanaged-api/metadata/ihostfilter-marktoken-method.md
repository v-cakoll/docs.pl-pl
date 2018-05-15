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
ms.openlocfilehash: 52375486eb9d7780a51808dedc5f876587efb115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="1312a-102">IHostFilter::MarkToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="1312a-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="1312a-103">Wskazuje token określonych metadanych zostaną przetworzone.</span><span class="sxs-lookup"><span data-stu-id="1312a-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1312a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1312a-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1312a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1312a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1312a-106">[in] Token metadanych do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="1312a-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1312a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1312a-107">Remarks</span></span>  
 <span data-ttu-id="1312a-108">Zwykle ma token do przetworzenia, jeśli znajduje się w zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="1312a-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="1312a-109">`MarkToken` Metody jest przekazywany do aparatu metadanych za pośrednictwem [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1312a-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1312a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1312a-110">Requirements</span></span>  
 <span data-ttu-id="1312a-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1312a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1312a-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1312a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1312a-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1312a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1312a-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1312a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1312a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1312a-115">See Also</span></span>  
 [<span data-ttu-id="1312a-116">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="1312a-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="1312a-117">IHostFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="1312a-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
