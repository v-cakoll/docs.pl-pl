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
ms.openlocfilehash: 9e26071181e8e0712c753fa03d5e16eb85e5ee68
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762839"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="6f6ce-102">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6f6ce-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="6f6ce-103">Dostarcza metody, które pozwalają hostowi jawnie zażądać, że środowisko uruchomieniowe języka wspólnego (CLR) tworzy nowe zadanie, pobiera aktualnie wykonywane zadanie i ustawia język geograficzny oraz kulturę dla zadania.</span><span class="sxs-lookup"><span data-stu-id="6f6ce-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f6ce-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6f6ce-104">Methods</span></span>  
  
|<span data-ttu-id="6f6ce-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6f6ce-105">Method</span></span>|<span data-ttu-id="6f6ce-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6f6ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f6ce-107">CreateTask, metoda</span><span class="sxs-lookup"><span data-stu-id="6f6ce-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="6f6ce-108">Żądania jawnie, że środowisko CLR tworzy nowe wystąpienie [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6f6ce-108">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="6f6ce-109">GetCurrentTask, metoda</span><span class="sxs-lookup"><span data-stu-id="6f6ce-109">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="6f6ce-110">Pobiera `ICLRTask` wystąpienie reprezentujące aktualnie wykonywane zadanie.</span><span class="sxs-lookup"><span data-stu-id="6f6ce-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="6f6ce-111">GetCurrentTaskType, metoda</span><span class="sxs-lookup"><span data-stu-id="6f6ce-111">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="6f6ce-112">Pobiera typ zadania, które jest aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="6f6ce-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="6f6ce-113">SetLocale, metoda</span><span class="sxs-lookup"><span data-stu-id="6f6ce-113">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="6f6ce-114">Powiadamia środowisko CLR o modyfikacji identyfikatora ustawień regionalnych w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="6f6ce-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="6f6ce-115">SetUILocale, metoda</span><span class="sxs-lookup"><span data-stu-id="6f6ce-115">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="6f6ce-116">Powiadamia środowisko uruchomieniowe języka wspólnego, że host zmodyfikował identyfikator ustawień regionalnych interfejsu użytkownika w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="6f6ce-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f6ce-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f6ce-117">Remarks</span></span>  
 <span data-ttu-id="6f6ce-118">Każde zadanie działające w środowisku hostowanym ma reprezentacje zarówno na stronie hosta (wystąpienie elementu [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)), jak i po stronie CLR (wystąpienie klasy [ICLRTask](iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="6f6ce-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="6f6ce-119">Host lub środowisko CLR mogą inicjować Tworzenie zadania, ale reprezentacja po stronie hosta musi być skojarzona z odpowiednią reprezentacją po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a środowiskiem CLR dotyczącym zadania.</span><span class="sxs-lookup"><span data-stu-id="6f6ce-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="6f6ce-120">Aby można było wykonać kod zarządzany w wątku systemu operacyjnego, należy utworzyć te dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="6f6ce-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f6ce-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f6ce-121">Requirements</span></span>  
 <span data-ttu-id="6f6ce-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f6ce-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f6ce-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6f6ce-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f6ce-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6f6ce-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f6ce-125">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f6ce-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6ce-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f6ce-126">See also</span></span>

- [<span data-ttu-id="6f6ce-127">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6f6ce-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="6f6ce-128">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f6ce-128">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="6f6ce-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f6ce-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="6f6ce-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6f6ce-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
