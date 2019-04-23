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
ms.openlocfilehash: 19ef7cb78791496de76e5741f8254ee88563c776
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134662"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="effc8-102">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="effc8-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="effc8-103">Znajdują się metody, które umożliwiają hosta do jawnego żądania, aby środowisko uruchomieniowe języka wspólnego (CLR) Utwórz nowe zadanie, Pobierz aktualnie wykonywane zadanie i geograficzne języka i kultury dla zadania.</span><span class="sxs-lookup"><span data-stu-id="effc8-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="effc8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="effc8-104">Methods</span></span>  
  
|<span data-ttu-id="effc8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="effc8-105">Method</span></span>|<span data-ttu-id="effc8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="effc8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="effc8-107">CreateTask, metoda</span><span class="sxs-lookup"><span data-stu-id="effc8-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="effc8-108">Żąda jawnie, że środowisko CLR, Utwórz nową [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="effc8-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="effc8-109">GetCurrentTask, metoda</span><span class="sxs-lookup"><span data-stu-id="effc8-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="effc8-110">Pobiera `ICLRTask` wystąpienia, która reprezentuje zadania, które jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="effc8-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="effc8-111">GetCurrentTaskType, metoda</span><span class="sxs-lookup"><span data-stu-id="effc8-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="effc8-112">Pobiera typ zadania, które jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="effc8-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="effc8-113">SetLocale, metoda</span><span class="sxs-lookup"><span data-stu-id="effc8-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="effc8-114">Powiadamia środowiska CLR, że host został zmodyfikowany identyfikator ustawień regionalnych na aktualnie wykonywane zadanie.</span><span class="sxs-lookup"><span data-stu-id="effc8-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="effc8-115">SetUILocale, metoda</span><span class="sxs-lookup"><span data-stu-id="effc8-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="effc8-116">Powiadamia środowiska uruchomieniowego języka wspólnego, że host został zmodyfikowany identyfikator ustawień regionalnych interfejsu użytkownika na aktualnie wykonywane zadanie.</span><span class="sxs-lookup"><span data-stu-id="effc8-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="effc8-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="effc8-117">Remarks</span></span>  
 <span data-ttu-id="effc8-118">Każde zadanie, który jest uruchomiony w środowisku hostowanej ma reprezentacji zarówno po stronie hosta (wystąpienie [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) i po stronie CLR (wystąpienie [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="effc8-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="effc8-119">Środowisko CLR lub hosta można zainicjować tworzenia zadania, ale reprezentacji po stronie hosta muszą być skojarzone z odpowiedniego reprezentacji po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a CLR dotyczące zadania.</span><span class="sxs-lookup"><span data-stu-id="effc8-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="effc8-120">Dwa obiekty muszą być tworzone i utworzyć ich kodu zarządzanego, można wykonać na wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="effc8-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="effc8-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="effc8-121">Requirements</span></span>  
 <span data-ttu-id="effc8-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="effc8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="effc8-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="effc8-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="effc8-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="effc8-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="effc8-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="effc8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effc8-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="effc8-126">See also</span></span>

- [<span data-ttu-id="effc8-127">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="effc8-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="effc8-128">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="effc8-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="effc8-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="effc8-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="effc8-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="effc8-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
