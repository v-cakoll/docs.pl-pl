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
ms.openlocfilehash: 22c3a480e2b68377e300df1083b3178ee4e2d2a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969861"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="f5f16-102">ICLRDebugManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5f16-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="f5f16-103">Udostępnia metody, które umożliwiają hosta skojarzyć zestaw zadań z identyfikatorem i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="f5f16-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5f16-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f5f16-104">Methods</span></span>  
  
|<span data-ttu-id="f5f16-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f5f16-105">Method</span></span>|<span data-ttu-id="f5f16-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f5f16-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5f16-107">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="f5f16-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="f5f16-108">Ustanawia nowego połączenia między hostem a debugera, aby skojarzyć zadania z identyfikatorem i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="f5f16-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="f5f16-109">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="f5f16-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="f5f16-110">Usuwa skojarzenie między listę zadań i identyfikatora oraz przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="f5f16-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="f5f16-111">GetDacl, metoda</span><span class="sxs-lookup"><span data-stu-id="f5f16-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="f5f16-112">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="f5f16-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="f5f16-113">IsDebuggerAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="f5f16-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="f5f16-114">Pobiera wartość wskazującą, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="f5f16-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="f5f16-115">SetConnectionTasks, metoda</span><span class="sxs-lookup"><span data-stu-id="f5f16-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="f5f16-116">Kojarzy listę [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpień przy użyciu identyfikatora i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="f5f16-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="f5f16-117">SetDacl, metoda</span><span class="sxs-lookup"><span data-stu-id="f5f16-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="f5f16-118">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="f5f16-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="f5f16-119">SetSymbolReadingPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="f5f16-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="f5f16-120">Ustawia zasady do odczytywania plików bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="f5f16-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="f5f16-121">Zasady określają, czy informacje o numery wierszy i pliki są uwzględniane w stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="f5f16-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5f16-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5f16-122">Remarks</span></span>  
 <span data-ttu-id="f5f16-123">Podczas debugowania scenariuszy, host może być grupowania zadań zgodnie z własną logikę programistyczną.</span><span class="sxs-lookup"><span data-stu-id="f5f16-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="f5f16-124">Na przykład grupowanie umożliwia deweloperem wyświetlić tylko zadania, które są wymagane przez interfejsy API dla deweloperów, zamiast zobaczyć zadanie, co zostało uruchomione w procesie.</span><span class="sxs-lookup"><span data-stu-id="f5f16-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="f5f16-125">`ICLRDebugManager` Zezwalaj hostowi na zaimplementować ten rodzaj grupowania.</span><span class="sxs-lookup"><span data-stu-id="f5f16-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5f16-126">Trzy `ICLRDebugManager` metod `BeginConnection`, `SetConnectionTasks` i `EndConnection`, są zależne od siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="f5f16-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="f5f16-127">One musi zostać wywołany w podanej kolejności, aby działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f5f16-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="f5f16-128">Grupowanie i identyfikatory i przyjaznych nazw hosta, przypisuje do grupowania, nie mają znaczenia dla środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f5f16-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="f5f16-129">Środowisko CLR jedynie przekazuje informacje o wzdłuż do debugera.</span><span class="sxs-lookup"><span data-stu-id="f5f16-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5f16-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5f16-130">Requirements</span></span>  
 <span data-ttu-id="f5f16-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5f16-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5f16-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5f16-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5f16-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5f16-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5f16-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f16-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f16-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5f16-135">See also</span></span>

- [<span data-ttu-id="f5f16-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f5f16-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
