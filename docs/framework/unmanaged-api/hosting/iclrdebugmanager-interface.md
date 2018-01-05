---
title: "ICLRDebugManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager
helpviewer_keywords: ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e712f22156e96cfc58e9c1a835077ba21ecd184
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="a06de-102">ICLRDebugManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a06de-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="a06de-103">Udostępnia metody umożliwiające hosta do skojarzenia z identyfikatorem i przyjazną nazwę zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="a06de-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a06de-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a06de-104">Methods</span></span>  
  
|<span data-ttu-id="a06de-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a06de-105">Method</span></span>|<span data-ttu-id="a06de-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a06de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a06de-107">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="a06de-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="a06de-108">Ustanawia nowego połączenia między hostem a debugera, aby skojarzyć zadania z identyfikatorem i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="a06de-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="a06de-109">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="a06de-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="a06de-110">Usuwa skojarzenie listę zadań przyjazną nazwę i identyfikator.</span><span class="sxs-lookup"><span data-stu-id="a06de-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="a06de-111">GetDacl, metoda</span><span class="sxs-lookup"><span data-stu-id="a06de-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="a06de-112">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="a06de-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="a06de-113">IsDebuggerAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="a06de-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="a06de-114">Pobiera wartość wskazującą, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="a06de-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="a06de-115">SetConnectionTasks, metoda</span><span class="sxs-lookup"><span data-stu-id="a06de-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="a06de-116">Kojarzy listę [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia o identyfikatorze i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="a06de-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="a06de-117">SetDacl, metoda</span><span class="sxs-lookup"><span data-stu-id="a06de-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="a06de-118">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="a06de-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="a06de-119">SetSymbolReadingPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="a06de-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="a06de-120">Ustawia zasady do odczytywania plików programu (PDB) bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a06de-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="a06de-121">Zasady określa, czy informacje dotyczące numerów wierszy i pliki są uwzględniane w stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="a06de-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a06de-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a06de-122">Remarks</span></span>  
 <span data-ttu-id="a06de-123">W scenariuszach debugowania hosta może być grupy zadań zgodnie z jego własnej logiki programowania.</span><span class="sxs-lookup"><span data-stu-id="a06de-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="a06de-124">Na przykład grupa umożliwia deweloperom wyświetlane zadania wymagane przez projektanta interfejsów API, zamiast każdego zadania uruchomione w procesie.</span><span class="sxs-lookup"><span data-stu-id="a06de-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="a06de-125">`ICLRDebugManager`Umożliwia hosta do wdrożenia tego rodzaju grupowania.</span><span class="sxs-lookup"><span data-stu-id="a06de-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a06de-126">Trzy `ICLRDebugManager` metod, `BeginConnection`, `SetConnectionTasks` i `EndConnection`, są zależne od siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="a06de-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="a06de-127">One musi zostać wywołany w podanej kolejności będzie działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="a06de-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="a06de-128">Grupowanie oraz identyfikatorów i przyjaznych nazw hosta przypisuje się do nieistniejącego grupowania mają znaczenia w przypadku środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a06de-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="a06de-129">Środowisko CLR jedynie przekazuje informacje o wzdłuż do debugera.</span><span class="sxs-lookup"><span data-stu-id="a06de-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a06de-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a06de-130">Requirements</span></span>  
 <span data-ttu-id="a06de-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a06de-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a06de-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a06de-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a06de-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a06de-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a06de-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a06de-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a06de-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a06de-135">See Also</span></span>  
 [<span data-ttu-id="a06de-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a06de-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
