---
title: "ICLRTaskManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager
helpviewer_keywords: ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 342d7b82802fcfbe9e179d85d6d692205f19e382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="003de-102">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="003de-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="003de-103">Znajdują się metod, które umożliwiają hosta, aby zażądać jawnie środowisko uruchomieniowe języka wspólnego (CLR) umożliwia utworzenie nowego zadania, Pobierz aktualnie wykonywanego zadania i geograficzne języka i kultury dla zadania.</span><span class="sxs-lookup"><span data-stu-id="003de-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="003de-104">Metody</span><span class="sxs-lookup"><span data-stu-id="003de-104">Methods</span></span>  
  
|<span data-ttu-id="003de-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="003de-105">Method</span></span>|<span data-ttu-id="003de-106">Opis</span><span class="sxs-lookup"><span data-stu-id="003de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="003de-107">CreateTask, metoda</span><span class="sxs-lookup"><span data-stu-id="003de-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="003de-108">Jawnie żądań, że środowisko CLR, Utwórz nową [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="003de-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="003de-109">GetCurrentTask, metoda</span><span class="sxs-lookup"><span data-stu-id="003de-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="003de-110">Pobiera `ICLRTask` wystąpienia reprezentujący zadanie, które jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="003de-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="003de-111">GetCurrentTaskType, metoda</span><span class="sxs-lookup"><span data-stu-id="003de-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="003de-112">Pobiera typ zadania, które jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="003de-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="003de-113">SetLocale, metoda</span><span class="sxs-lookup"><span data-stu-id="003de-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="003de-114">Powiadamia CLR, że host został zmodyfikowany identyfikator ustawień regionalnych na aktualnie wykonywanego zadania.</span><span class="sxs-lookup"><span data-stu-id="003de-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="003de-115">SetUILocale, metoda</span><span class="sxs-lookup"><span data-stu-id="003de-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="003de-116">Powiadamia środowisko uruchomieniowe języka wspólnego, że host został zmodyfikowany identyfikator ustawień regionalnych interfejsu użytkownika na aktualnie wykonywanego zadania.</span><span class="sxs-lookup"><span data-stu-id="003de-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="003de-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="003de-117">Remarks</span></span>  
 <span data-ttu-id="003de-118">Każde zadanie, który jest uruchomiony w środowisku hostowanej ma reprezentacje zarówno po stronie hosta (wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) i po stronie CLR (wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="003de-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="003de-119">Host lub CLR można inicjować tworzenia zadania, ale reprezentacja po stronie hosta musi być skojarzony z odpowiedniego reprezentacja po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a CLR dotyczące zadania.</span><span class="sxs-lookup"><span data-stu-id="003de-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="003de-120">Dwa obiekty należy utworzyć i utworzyć kod zarządzany może zostać uruchomiony w wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="003de-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="003de-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="003de-121">Requirements</span></span>  
 <span data-ttu-id="003de-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="003de-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="003de-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="003de-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="003de-124">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="003de-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="003de-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="003de-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="003de-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="003de-126">See Also</span></span>  
 [<span data-ttu-id="003de-127">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="003de-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="003de-128">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="003de-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="003de-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="003de-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="003de-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="003de-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
