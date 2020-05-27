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
ms.openlocfilehash: e8cb1486ccea11ba6edcf7bbb781a9bf210b496d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804903"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="19d8b-102">IHostCrst — Interfejs</span><span class="sxs-lookup"><span data-stu-id="19d8b-102">IHostCrst Interface</span></span>
<span data-ttu-id="19d8b-103">Służy jako reprezentacja hosta sekcji krytycznej dla wątków.</span><span class="sxs-lookup"><span data-stu-id="19d8b-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19d8b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="19d8b-104">Methods</span></span>  
  
|<span data-ttu-id="19d8b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="19d8b-105">Method</span></span>|<span data-ttu-id="19d8b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="19d8b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19d8b-107">Enter, metoda</span><span class="sxs-lookup"><span data-stu-id="19d8b-107">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="19d8b-108">Wprowadza sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="19d8b-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="19d8b-109">Leave, metoda</span><span class="sxs-lookup"><span data-stu-id="19d8b-109">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="19d8b-110">Pozostawia sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="19d8b-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="19d8b-111">SetSpinCount, metoda</span><span class="sxs-lookup"><span data-stu-id="19d8b-111">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="19d8b-112">Ustawia liczbę obrotów dla sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="19d8b-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="19d8b-113">TryEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="19d8b-113">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="19d8b-114">Próbuje wprowadzić sekcję krytyczną i natychmiast raportuje powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="19d8b-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19d8b-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19d8b-115">Remarks</span></span>  
 <span data-ttu-id="19d8b-116">`IHostCrst`zezwala, aby środowisko uruchomieniowe języka wspólnego (CLR) komunikować się bezpośrednio z reprezentacją w sekcji krytycznej hosta, a nie przy użyciu funkcji Win32, takich jak `EnterCriticalSection` lub `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="19d8b-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19d8b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19d8b-117">Requirements</span></span>  
 <span data-ttu-id="19d8b-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19d8b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19d8b-119">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19d8b-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19d8b-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="19d8b-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19d8b-121">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19d8b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d8b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19d8b-122">See also</span></span>

- [<span data-ttu-id="19d8b-123">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="19d8b-123">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="19d8b-124">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="19d8b-124">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="19d8b-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="19d8b-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
