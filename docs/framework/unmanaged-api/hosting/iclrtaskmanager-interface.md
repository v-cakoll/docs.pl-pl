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
ms.openlocfilehash: e25a6a03a836b8b4964b8260c974c8e8d8d9998d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092187"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="bad15-102">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bad15-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="bad15-103">Dostarcza metody, które pozwalają hostowi jawnie zażądać, że środowisko uruchomieniowe języka wspólnego (CLR) tworzy nowe zadanie, pobiera aktualnie wykonywane zadanie i ustawia język geograficzny oraz kulturę dla zadania.</span><span class="sxs-lookup"><span data-stu-id="bad15-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bad15-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bad15-104">Methods</span></span>  
  
|<span data-ttu-id="bad15-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bad15-105">Method</span></span>|<span data-ttu-id="bad15-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bad15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bad15-107">CreateTask, metoda</span><span class="sxs-lookup"><span data-stu-id="bad15-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="bad15-108">Żądania jawnie, że środowisko CLR tworzy nowe wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bad15-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="bad15-109">GetCurrentTask, metoda</span><span class="sxs-lookup"><span data-stu-id="bad15-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="bad15-110">Pobiera wystąpienie `ICLRTask`, które reprezentuje aktualnie wykonywane zadanie.</span><span class="sxs-lookup"><span data-stu-id="bad15-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="bad15-111">GetCurrentTaskType, metoda</span><span class="sxs-lookup"><span data-stu-id="bad15-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="bad15-112">Pobiera typ zadania, które jest aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="bad15-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="bad15-113">SetLocale, metoda</span><span class="sxs-lookup"><span data-stu-id="bad15-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="bad15-114">Powiadamia środowisko CLR o modyfikacji identyfikatora ustawień regionalnych w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="bad15-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="bad15-115">SetUILocale, metoda</span><span class="sxs-lookup"><span data-stu-id="bad15-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="bad15-116">Powiadamia środowisko uruchomieniowe języka wspólnego, że host zmodyfikował identyfikator ustawień regionalnych interfejsu użytkownika w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="bad15-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bad15-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bad15-117">Remarks</span></span>  
 <span data-ttu-id="bad15-118">Każde zadanie działające w środowisku hostowanym ma reprezentacje zarówno na stronie hosta (wystąpienie elementu [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)), jak i po stronie CLR (wystąpienie klasy [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="bad15-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="bad15-119">Host lub środowisko CLR mogą inicjować Tworzenie zadania, ale reprezentacja po stronie hosta musi być skojarzona z odpowiednią reprezentacją po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a środowiskiem CLR dotyczącym zadania.</span><span class="sxs-lookup"><span data-stu-id="bad15-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="bad15-120">Aby można było wykonać kod zarządzany w wątku systemu operacyjnego, należy utworzyć te dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="bad15-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bad15-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bad15-121">Requirements</span></span>  
 <span data-ttu-id="bad15-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bad15-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bad15-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bad15-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bad15-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bad15-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bad15-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bad15-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad15-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bad15-126">See also</span></span>

- [<span data-ttu-id="bad15-127">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="bad15-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="bad15-128">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="bad15-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bad15-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bad15-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="bad15-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bad15-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
