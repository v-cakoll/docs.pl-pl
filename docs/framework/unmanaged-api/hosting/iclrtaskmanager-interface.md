---
title: ICLRTaskManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9012a38271afdef5e00e9e69eb9b2730834be2fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656157"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="f83b1-102">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f83b1-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="f83b1-103">Znajdują się metody, które umożliwiają hosta do jawnego żądania, aby środowisko uruchomieniowe języka wspólnego (CLR) Utwórz nowe zadanie, Pobierz aktualnie wykonywane zadanie i geograficzne języka i kultury dla zadania.</span><span class="sxs-lookup"><span data-stu-id="f83b1-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f83b1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f83b1-104">Methods</span></span>  
  
|<span data-ttu-id="f83b1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f83b1-105">Method</span></span>|<span data-ttu-id="f83b1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f83b1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f83b1-107">CreateTask, metoda</span><span class="sxs-lookup"><span data-stu-id="f83b1-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="f83b1-108">Żąda jawnie, że środowisko CLR, Utwórz nową [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f83b1-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="f83b1-109">GetCurrentTask, metoda</span><span class="sxs-lookup"><span data-stu-id="f83b1-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="f83b1-110">Pobiera `ICLRTask` wystąpienia, która reprezentuje zadania, które jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f83b1-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="f83b1-111">GetCurrentTaskType, metoda</span><span class="sxs-lookup"><span data-stu-id="f83b1-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="f83b1-112">Pobiera typ zadania, które jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f83b1-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="f83b1-113">SetLocale, metoda</span><span class="sxs-lookup"><span data-stu-id="f83b1-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="f83b1-114">Powiadamia środowiska CLR, że host został zmodyfikowany identyfikator ustawień regionalnych na aktualnie wykonywane zadanie.</span><span class="sxs-lookup"><span data-stu-id="f83b1-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="f83b1-115">SetUILocale, metoda</span><span class="sxs-lookup"><span data-stu-id="f83b1-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="f83b1-116">Powiadamia środowiska uruchomieniowego języka wspólnego, że host został zmodyfikowany identyfikator ustawień regionalnych interfejsu użytkownika na aktualnie wykonywane zadanie.</span><span class="sxs-lookup"><span data-stu-id="f83b1-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f83b1-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f83b1-117">Remarks</span></span>  
 <span data-ttu-id="f83b1-118">Każde zadanie, który jest uruchomiony w środowisku hostowanej ma reprezentacji zarówno po stronie hosta (wystąpienie [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) i po stronie CLR (wystąpienie [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="f83b1-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="f83b1-119">Środowisko CLR lub hosta można zainicjować tworzenia zadania, ale reprezentacji po stronie hosta muszą być skojarzone z odpowiedniego reprezentacji po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a CLR dotyczące zadania.</span><span class="sxs-lookup"><span data-stu-id="f83b1-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="f83b1-120">Dwa obiekty muszą być tworzone i utworzyć ich kodu zarządzanego, można wykonać na wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f83b1-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f83b1-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f83b1-121">Requirements</span></span>  
 <span data-ttu-id="f83b1-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f83b1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f83b1-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f83b1-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f83b1-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f83b1-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f83b1-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f83b1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f83b1-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f83b1-126">See also</span></span>
- [<span data-ttu-id="f83b1-127">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f83b1-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f83b1-128">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f83b1-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f83b1-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f83b1-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="f83b1-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f83b1-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
