---
title: IGCThreadControl::SuspensionEnding — Metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90b0cba50129bc728089e41ece5a30697cfc3bc5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144420"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="67b81-102">IGCThreadControl::SuspensionEnding — Metoda</span><span class="sxs-lookup"><span data-stu-id="67b81-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="67b81-103">Powiadamia hosta, czy środowisko uruchomieniowe jest wznawianie wątków po wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="67b81-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67b81-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67b81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="67b81-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="67b81-106">[in] Generowanie, na którym została wykonana wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="67b81-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67b81-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67b81-107">Remarks</span></span>  
 <span data-ttu-id="67b81-108">Nie zmienić termin egzaminu żadnych wątków podczas `SuspensionEnding` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="67b81-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67b81-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67b81-109">Requirements</span></span>  
 <span data-ttu-id="67b81-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67b81-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67b81-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="67b81-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67b81-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="67b81-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67b81-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67b81-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b81-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67b81-114">See also</span></span>

- [<span data-ttu-id="67b81-115">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="67b81-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
