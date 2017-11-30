---
title: "EMemoryCriticalLevel — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15a6786cb99a64d441d7e05fb91cd8ff0f3af92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="abde3-102">EMemoryCriticalLevel — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="abde3-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="abde3-103">Zawiera wartości, które wskazują wpływ awarii podczas alokacji pamięci wysłano żądanie, ale nie mogą zostać spełnione.</span><span class="sxs-lookup"><span data-stu-id="abde3-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abde3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abde3-104">Syntax</span></span>  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="abde3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="abde3-105">Members</span></span>  
  
|<span data-ttu-id="abde3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="abde3-106">Member</span></span>|<span data-ttu-id="abde3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="abde3-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="abde3-108">Wskazuje, że przydział ma decydujące znaczenie dla wykonywania kodu zarządzanego w domenie, do której wysłano żądanie alokacji.</span><span class="sxs-lookup"><span data-stu-id="abde3-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="abde3-109">Jeśli nie można przydzielić pamięci, CLR nie może zagwarantować, że domena jest nadal można używać.</span><span class="sxs-lookup"><span data-stu-id="abde3-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="abde3-110">Host decyduje o tym, jakie działania w sytuacji, gdy nie mogą być spełnione alokacji.</span><span class="sxs-lookup"><span data-stu-id="abde3-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="abde3-111">Może spowodować, żeby CLR aby przerwać `AppDomain` automatycznie, lub zezwalanie na kontynuowanie działania przez wywołanie metody na [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="abde3-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="abde3-112">Wskazuje, że przydział jest krytyczne w wykonywaniu kodu zarządzanego w procesie.</span><span class="sxs-lookup"><span data-stu-id="abde3-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="abde3-113">Ta wartość jest używana podczas uruchamiania i podczas uruchamiania finalizatory.</span><span class="sxs-lookup"><span data-stu-id="abde3-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="abde3-114">Jeśli nie można przydzielić pamięci, CLR nie może działać w procesie.</span><span class="sxs-lookup"><span data-stu-id="abde3-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="abde3-115">Jeśli alokacja nie powiedzie się, CLR skutecznie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="abde3-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="abde3-116">Wszystkie kolejne wywołania do środowiska CLR się niepowodzeniem z HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="abde3-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="abde3-117">Wskazuje, że przydział jest krytyczne do uruchomienia zadania, który zgłosił żądanie alokacji.</span><span class="sxs-lookup"><span data-stu-id="abde3-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="abde3-118">Jeśli nie można przydzielić pamięci, CLR nie może zagwarantować, można wykonać zadania.</span><span class="sxs-lookup"><span data-stu-id="abde3-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="abde3-119">W przypadku awarii, zgłasza CLR <xref:System.Threading.ThreadAbortException> w wątku systemu fizycznego operacji.</span><span class="sxs-lookup"><span data-stu-id="abde3-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abde3-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abde3-120">Remarks</span></span>  
 <span data-ttu-id="abde3-121">Metody alokacji pamięci, które są zdefiniowane w [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) i [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfejsy zająć parametr tego typu.</span><span class="sxs-lookup"><span data-stu-id="abde3-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="abde3-122">W zależności od ważności awarii hosta można zdecydować, czy niepowodzenie żądanie alokacji natychmiast lub poczekać, aż można spełnić.</span><span class="sxs-lookup"><span data-stu-id="abde3-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abde3-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abde3-123">Requirements</span></span>  
 <span data-ttu-id="abde3-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abde3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abde3-125">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="abde3-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abde3-126">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abde3-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abde3-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abde3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abde3-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abde3-128">See Also</span></span>  
 [<span data-ttu-id="abde3-129">ICLRMemoryNotificationCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="abde3-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="abde3-130">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="abde3-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
