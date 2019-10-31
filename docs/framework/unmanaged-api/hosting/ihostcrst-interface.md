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
ms.openlocfilehash: 108492ba298e9f8429b2acd890ab3404365bc602
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130524"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="41814-102">IHostCrst — Interfejs</span><span class="sxs-lookup"><span data-stu-id="41814-102">IHostCrst Interface</span></span>
<span data-ttu-id="41814-103">Służy jako reprezentacja hosta sekcji krytycznej dla wątków.</span><span class="sxs-lookup"><span data-stu-id="41814-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41814-104">Metody</span><span class="sxs-lookup"><span data-stu-id="41814-104">Methods</span></span>  
  
|<span data-ttu-id="41814-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="41814-105">Method</span></span>|<span data-ttu-id="41814-106">Opis</span><span class="sxs-lookup"><span data-stu-id="41814-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41814-107">Enter, metoda</span><span class="sxs-lookup"><span data-stu-id="41814-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="41814-108">Wprowadza sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="41814-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="41814-109">Leave, metoda</span><span class="sxs-lookup"><span data-stu-id="41814-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="41814-110">Pozostawia sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="41814-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="41814-111">SetSpinCount, metoda</span><span class="sxs-lookup"><span data-stu-id="41814-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="41814-112">Ustawia liczbę obrotów dla sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="41814-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="41814-113">TryEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="41814-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="41814-114">Próbuje wprowadzić sekcję krytyczną i natychmiast raportuje powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="41814-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41814-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41814-115">Remarks</span></span>  
 <span data-ttu-id="41814-116">`IHostCrst` umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do bezpośredniego komunikowania się z reprezentacją sekcji krytycznej hosta, a nie za pomocą funkcji Win32, takich jak `EnterCriticalSection` lub `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="41814-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41814-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41814-117">Requirements</span></span>  
 <span data-ttu-id="41814-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41814-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41814-119">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41814-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41814-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="41814-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41814-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41814-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41814-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41814-122">See also</span></span>

- [<span data-ttu-id="41814-123">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="41814-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="41814-124">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="41814-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="41814-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="41814-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
