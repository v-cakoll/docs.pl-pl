---
title: IGCHost::Collect — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bce005a677dcb74c176a6dddfb2726f6b1fd0e8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436910"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="4be34-102">IGCHost::Collect — Metoda</span><span class="sxs-lookup"><span data-stu-id="4be34-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="4be34-103">Wymusza kolekcji wystąpi dla danego generacji, bez względu na stan bieżący wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4be34-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4be34-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4be34-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4be34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4be34-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="4be34-106">[in] Generowanie, na którym należy wykonać wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4be34-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="4be34-107">Wartość -1 wskazuje, że wszystkie generacje zostaną poddane wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4be34-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4be34-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4be34-108">Requirements</span></span>  
 <span data-ttu-id="4be34-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4be34-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4be34-110">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="4be34-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="4be34-111">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4be34-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4be34-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4be34-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be34-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4be34-113">See Also</span></span>  
 [<span data-ttu-id="4be34-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="4be34-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
