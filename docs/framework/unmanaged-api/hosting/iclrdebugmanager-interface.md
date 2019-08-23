---
title: ICLRDebugManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a408995793caf879f8d5624ab727102c4859195
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959613"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="71d35-102">ICLRDebugManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="71d35-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="71d35-103">Dostarcza metody, które umożliwiają hostowi kojarzenie zestawu zadań z identyfikatorem i przyjazną nazwą.</span><span class="sxs-lookup"><span data-stu-id="71d35-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71d35-104">Metody</span><span class="sxs-lookup"><span data-stu-id="71d35-104">Methods</span></span>  
  
|<span data-ttu-id="71d35-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="71d35-105">Method</span></span>|<span data-ttu-id="71d35-106">Opis</span><span class="sxs-lookup"><span data-stu-id="71d35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71d35-107">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="71d35-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="71d35-108">Ustanawia nowe połączenie między hostem i debugerem w celu kojarzenia zadań z identyfikatorem i przyjazną nazwą.</span><span class="sxs-lookup"><span data-stu-id="71d35-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="71d35-109">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="71d35-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="71d35-110">Usuwa skojarzenie między listą zadań i identyfikatorem i przyjazną nazwą.</span><span class="sxs-lookup"><span data-stu-id="71d35-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="71d35-111">GetDacl, metoda</span><span class="sxs-lookup"><span data-stu-id="71d35-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="71d35-112">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="71d35-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="71d35-113">IsDebuggerAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="71d35-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="71d35-114">Pobiera wartość wskazującą, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="71d35-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="71d35-115">SetConnectionTasks, metoda</span><span class="sxs-lookup"><span data-stu-id="71d35-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="71d35-116">Kojarzy listę wystąpień [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) z identyfikatorem i przyjazną nazwą.</span><span class="sxs-lookup"><span data-stu-id="71d35-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="71d35-117">SetDacl, metoda</span><span class="sxs-lookup"><span data-stu-id="71d35-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="71d35-118">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="71d35-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="71d35-119">SetSymbolReadingPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="71d35-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="71d35-120">Ustawia zasady odczytywania plików bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="71d35-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="71d35-121">Zasady określają, czy informacje o numerach wierszy i plikach są zawarte w stosach wywołań.</span><span class="sxs-lookup"><span data-stu-id="71d35-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71d35-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71d35-122">Remarks</span></span>  
 <span data-ttu-id="71d35-123">W scenariuszach debugowania host może chcieć grupować zadania zgodnie z własną logiką programowania.</span><span class="sxs-lookup"><span data-stu-id="71d35-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="71d35-124">Na przykład zgrupowanie zezwoli deweloperowi na wyświetlanie tylko zadań wymaganych przez interfejsy API dewelopera, a nie oglądanie wszystkich zadań uruchomionych w procesie.</span><span class="sxs-lookup"><span data-stu-id="71d35-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="71d35-125">`ICLRDebugManager`zezwala hostowi na wdrożenie tego rodzaju grupowania.</span><span class="sxs-lookup"><span data-stu-id="71d35-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="71d35-126">Trzy `ICLRDebugManager` metody, `BeginConnection`, `SetConnectionTasks` i`EndConnection`, są zależne od siebie.</span><span class="sxs-lookup"><span data-stu-id="71d35-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="71d35-127">Muszą być wywoływane w danej kolejności, aby działały zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="71d35-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="71d35-128">Grupowanie i identyfikatory oraz przyjazne nazwy przypisywane przez hosta do grupy nie mają znaczenia dla środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="71d35-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="71d35-129">Środowisko CLR jedynie przekazuje informacje wraz z debugerem.</span><span class="sxs-lookup"><span data-stu-id="71d35-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d35-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71d35-130">Requirements</span></span>  
 <span data-ttu-id="71d35-131">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71d35-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71d35-132">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="71d35-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71d35-133">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="71d35-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71d35-134">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71d35-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d35-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71d35-135">See also</span></span>

- [<span data-ttu-id="71d35-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="71d35-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
