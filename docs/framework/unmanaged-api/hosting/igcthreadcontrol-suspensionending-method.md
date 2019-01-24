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
ms.openlocfilehash: d77380e35d8f5eee1e50b1030493e0b17cbadfba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713291"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="5a3fb-102">IGCThreadControl::SuspensionEnding — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a3fb-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="5a3fb-103">Powiadamia hosta, czy środowisko uruchomieniowe jest wznawianie wątków po wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="5a3fb-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a3fb-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a3fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a3fb-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="5a3fb-106">[in] Generowanie, na którym została wykonana wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5a3fb-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a3fb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a3fb-107">Remarks</span></span>  
 <span data-ttu-id="5a3fb-108">Nie zmienić termin egzaminu żadnych wątków podczas `SuspensionEnding` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5a3fb-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a3fb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a3fb-109">Requirements</span></span>  
 <span data-ttu-id="5a3fb-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a3fb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a3fb-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a3fb-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a3fb-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a3fb-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a3fb-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a3fb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a3fb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a3fb-114">See also</span></span>
- [<span data-ttu-id="5a3fb-115">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a3fb-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
