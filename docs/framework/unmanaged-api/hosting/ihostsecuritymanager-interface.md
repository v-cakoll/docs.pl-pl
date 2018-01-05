---
title: "IHostSecurityManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager
helpviewer_keywords: IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44f2272c0f4e1423c222a004559d7bbd58237d82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="6f16b-102">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6f16b-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="6f16b-103">Udostępnia metody, które umożliwiają dostęp do i kontrolę nad wątku aktualnie wykonywane w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6f16b-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f16b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6f16b-104">Methods</span></span>  
  
|<span data-ttu-id="6f16b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6f16b-105">Method</span></span>|<span data-ttu-id="6f16b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6f16b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f16b-107">GetSecurityContext, metoda</span><span class="sxs-lookup"><span data-stu-id="6f16b-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="6f16b-108">Pobiera żądanie [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.</span><span class="sxs-lookup"><span data-stu-id="6f16b-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="6f16b-109">ImpersonateLoggedOnUser, metoda</span><span class="sxs-lookup"><span data-stu-id="6f16b-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="6f16b-110">Żądania który kodu można wykonać przy użyciu poświadczeń Bieżąca tożsamość użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6f16b-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="6f16b-111">OpenThreadToken, metoda</span><span class="sxs-lookup"><span data-stu-id="6f16b-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="6f16b-112">Otwiera token dostępu skojarzone z bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="6f16b-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="6f16b-113">RevertToSelf, metoda</span><span class="sxs-lookup"><span data-stu-id="6f16b-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="6f16b-114">Przerywa personifikacji bieżącej tożsamości użytkownika i zwraca oryginalnego tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="6f16b-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="6f16b-115">SetSecurityContext, metoda</span><span class="sxs-lookup"><span data-stu-id="6f16b-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="6f16b-116">Ustawia kontekst zabezpieczeń dla wątku aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="6f16b-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="6f16b-117">SetThreadToken, metoda</span><span class="sxs-lookup"><span data-stu-id="6f16b-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="6f16b-118">Ustawia dojście wątku aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="6f16b-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f16b-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f16b-119">Remarks</span></span>  
 <span data-ttu-id="6f16b-120">Hosta można kontrolować kod dostęp do tokenów wątku przez środowisko uruchomieniowe języka wspólnego (CLR) i kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6f16b-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="6f16b-121">Zapewnia również Zabezpieczenia pełne informacje o kontekście jest przekazywany przez operacje asynchroniczne lub punktów kodowych z ograniczeniami kod dostępu.</span><span class="sxs-lookup"><span data-stu-id="6f16b-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="6f16b-122">`IHostSecurityContext`hermetyzuje informacje kontekstu zabezpieczeń, które jest nieprzezroczysta dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="6f16b-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="6f16b-123">Środowisko CLR wewnętrznie obsługuje kontekstu zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="6f16b-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="6f16b-124">Wysyła zapytanie dotyczące procesu `IHostSecurityManager` w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="6f16b-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
-   <span data-ttu-id="6f16b-125">W wątku finalizatora podczas wykonywania finalizatora.</span><span class="sxs-lookup"><span data-stu-id="6f16b-125">On the finalizer thread, during finalizer execution.</span></span>  
  
-   <span data-ttu-id="6f16b-126">Podczas wykonywania konstruktora klasy i modułu.</span><span class="sxs-lookup"><span data-stu-id="6f16b-126">During class and module constructor execution.</span></span>  
  
-   <span data-ttu-id="6f16b-127">W punktach asynchronicznych w wątku roboczego w wywołaniach [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6f16b-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
-   <span data-ttu-id="6f16b-128">W obsługę portów We/Wy.</span><span class="sxs-lookup"><span data-stu-id="6f16b-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f16b-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f16b-129">Requirements</span></span>  
 <span data-ttu-id="6f16b-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f16b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f16b-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f16b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f16b-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f16b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f16b-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f16b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f16b-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f16b-134">See Also</span></span>  
 [<span data-ttu-id="6f16b-135">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f16b-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="6f16b-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6f16b-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
