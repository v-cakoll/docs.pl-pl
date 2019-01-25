---
title: IHostCrst — Interfejs
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34a911668db09b255282833cec3e6272b315373b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618662"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="6cfd3-102">IHostCrst — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6cfd3-102">IHostCrst Interface</span></span>
<span data-ttu-id="6cfd3-103">Służy jako hosta reprezentacja sekcję krytyczną dla wątków.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cfd3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6cfd3-104">Methods</span></span>  
  
|<span data-ttu-id="6cfd3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6cfd3-105">Method</span></span>|<span data-ttu-id="6cfd3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6cfd3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cfd3-107">Enter, metoda</span><span class="sxs-lookup"><span data-stu-id="6cfd3-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="6cfd3-108">Wprowadza sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="6cfd3-109">Leave, metoda</span><span class="sxs-lookup"><span data-stu-id="6cfd3-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="6cfd3-110">Pozostawia sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="6cfd3-111">SetSpinCount, metoda</span><span class="sxs-lookup"><span data-stu-id="6cfd3-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="6cfd3-112">Ustawia liczbę pokrętła sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="6cfd3-113">TryEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="6cfd3-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="6cfd3-114">Próbuje wprowadzić sekcję krytyczną i raporty o powodzeniu lub niepowodzeniu natychmiast.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cfd3-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cfd3-115">Remarks</span></span>  
 <span data-ttu-id="6cfd3-116">`IHostCrst` Umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do bezpośredniego komunikowania się z hosta reprezentacja sekcję krytyczną, a nie przy użyciu funkcji środowiska Win32, takich jak `EnterCriticalSection` lub `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cfd3-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6cfd3-117">Requirements</span></span>  
 <span data-ttu-id="6cfd3-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cfd3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cfd3-119">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cfd3-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cfd3-120">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cfd3-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cfd3-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cfd3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfd3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cfd3-122">See also</span></span>
- [<span data-ttu-id="6cfd3-123">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cfd3-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6cfd3-124">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cfd3-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="6cfd3-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6cfd3-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
