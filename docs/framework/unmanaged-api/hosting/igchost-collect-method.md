---
title: "IGCHost::Collect — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.Collect
api_location: mscoree.dll
api_type: COM
f1_keywords: Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a0ffe759c6c6049baa11dcc00d4cdee8415156f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="igchostcollect-method"></a><span data-ttu-id="82b15-102">IGCHost::Collect — Metoda</span><span class="sxs-lookup"><span data-stu-id="82b15-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="82b15-103">Wymusza kolekcji wystąpi dla danego generacji, bez względu na stan bieżący wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="82b15-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b15-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82b15-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82b15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82b15-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="82b15-106">[in] Generowanie, na którym należy wykonać wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="82b15-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="82b15-107">Wartość -1 wskazuje, że wszystkie generacje zostaną poddane wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="82b15-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82b15-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82b15-108">Requirements</span></span>  
 <span data-ttu-id="82b15-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82b15-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82b15-110">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="82b15-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="82b15-111">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82b15-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82b15-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82b15-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82b15-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82b15-113">See Also</span></span>  
 [<span data-ttu-id="82b15-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="82b15-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
