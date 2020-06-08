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
ms.openlocfilehash: f918d4e7b95922734d70ed832581e6c494c70b05
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501641"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="a7b77-102">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7b77-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="a7b77-103">Dostarcza metody, które pozwalają hostowi jawnie zażądać, że środowisko uruchomieniowe języka wspólnego (CLR) tworzy nowe zadanie, pobiera aktualnie wykonywane zadanie i ustawia język geograficzny oraz kulturę dla zadania.</span><span class="sxs-lookup"><span data-stu-id="a7b77-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7b77-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a7b77-104">Methods</span></span>  
  
|<span data-ttu-id="a7b77-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a7b77-105">Method</span></span>|<span data-ttu-id="a7b77-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a7b77-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7b77-107">CreateTask, metoda</span><span class="sxs-lookup"><span data-stu-id="a7b77-107">CreateTask Method</span></span>](iclrtaskmanager-createtask-method.md)|<span data-ttu-id="a7b77-108">Żądania jawnie, że środowisko CLR tworzy nowe wystąpienie [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a7b77-108">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="a7b77-109">GetCurrentTask, metoda</span><span class="sxs-lookup"><span data-stu-id="a7b77-109">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="a7b77-110">Pobiera `ICLRTask` wystąpienie reprezentujące aktualnie wykonywane zadanie.</span><span class="sxs-lookup"><span data-stu-id="a7b77-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="a7b77-111">GetCurrentTaskType, metoda</span><span class="sxs-lookup"><span data-stu-id="a7b77-111">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="a7b77-112">Pobiera typ zadania, które jest aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="a7b77-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="a7b77-113">SetLocale, metoda</span><span class="sxs-lookup"><span data-stu-id="a7b77-113">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="a7b77-114">Powiadamia środowisko CLR o modyfikacji identyfikatora ustawień regionalnych w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="a7b77-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="a7b77-115">SetUILocale, metoda</span><span class="sxs-lookup"><span data-stu-id="a7b77-115">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="a7b77-116">Powiadamia środowisko uruchomieniowe języka wspólnego, że host zmodyfikował identyfikator ustawień regionalnych interfejsu użytkownika w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="a7b77-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7b77-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7b77-117">Remarks</span></span>  
 <span data-ttu-id="a7b77-118">Każde zadanie działające w środowisku hostowanym ma reprezentacje zarówno na stronie hosta (wystąpienie elementu [IHostTask](ihosttask-interface.md)), jak i po stronie CLR (wystąpienie klasy [ICLRTask](iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="a7b77-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="a7b77-119">Host lub środowisko CLR mogą inicjować Tworzenie zadania, ale reprezentacja po stronie hosta musi być skojarzona z odpowiednią reprezentacją po stronie CLR w celu zapewnienia pomyślnej komunikacji między hostem a środowiskiem CLR dotyczącym zadania.</span><span class="sxs-lookup"><span data-stu-id="a7b77-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="a7b77-120">Aby można było wykonać kod zarządzany w wątku systemu operacyjnego, należy utworzyć te dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="a7b77-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b77-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7b77-121">Requirements</span></span>  
 <span data-ttu-id="a7b77-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7b77-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7b77-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a7b77-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7b77-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a7b77-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7b77-125">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7b77-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b77-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7b77-126">See also</span></span>

- [<span data-ttu-id="a7b77-127">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7b77-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a7b77-128">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7b77-128">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a7b77-129">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7b77-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="a7b77-130">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a7b77-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
