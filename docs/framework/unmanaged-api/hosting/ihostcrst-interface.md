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
ms.openlocfilehash: 88f2ef8299911905d651ad5c3076dc9c74f397f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="bb640-102">IHostCrst — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bb640-102">IHostCrst Interface</span></span>
<span data-ttu-id="bb640-103">Służy jako hosta reprezentację sekcja krytyczna dla wątków.</span><span class="sxs-lookup"><span data-stu-id="bb640-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb640-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bb640-104">Methods</span></span>  
  
|<span data-ttu-id="bb640-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bb640-105">Method</span></span>|<span data-ttu-id="bb640-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bb640-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb640-107">Enter, metoda</span><span class="sxs-lookup"><span data-stu-id="bb640-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="bb640-108">Wprowadza sekcja krytyczna.</span><span class="sxs-lookup"><span data-stu-id="bb640-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="bb640-109">Leave, metoda</span><span class="sxs-lookup"><span data-stu-id="bb640-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="bb640-110">Pozostawia sekcja krytyczna.</span><span class="sxs-lookup"><span data-stu-id="bb640-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="bb640-111">SetSpinCount, metoda</span><span class="sxs-lookup"><span data-stu-id="bb640-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="bb640-112">Ustawia liczbę pokrętła dla sekcji krytycznych.</span><span class="sxs-lookup"><span data-stu-id="bb640-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="bb640-113">TryEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="bb640-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="bb640-114">Próbuje natychmiast wprowadź sekcja krytyczna i raporty powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="bb640-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb640-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb640-115">Remarks</span></span>  
 <span data-ttu-id="bb640-116">`IHostCrst` Umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do bezpośredniego komunikowania się z hosta reprezentację sekcja krytyczna, a nie przy użyciu funkcji Win32, takich jak `EnterCriticalSection` lub `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="bb640-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb640-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb640-117">Requirements</span></span>  
 <span data-ttu-id="bb640-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb640-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb640-119">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb640-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb640-120">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb640-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb640-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb640-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb640-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb640-122">See Also</span></span>  
 [<span data-ttu-id="bb640-123">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb640-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="bb640-124">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb640-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="bb640-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bb640-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
