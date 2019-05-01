---
title: EMemoryCriticalLevel — Wyliczenie
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ee8705d00e1f63f69863d0bf8e7d0d9d62807e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968613"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="d4020-102">EMemoryCriticalLevel — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d4020-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="d4020-103">Zawiera wartości, które wskazują wpływ awarii, gdy zażądano alokacji pamięci, ale nie mogą zostać spełnione.</span><span class="sxs-lookup"><span data-stu-id="d4020-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4020-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4020-104">Syntax</span></span>  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="d4020-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d4020-105">Members</span></span>  
  
|<span data-ttu-id="d4020-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d4020-106">Member</span></span>|<span data-ttu-id="d4020-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d4020-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="d4020-108">Wskazuje, czy przydział jest istotne w przypadku wykonywania kodu zarządzanego w domenie, który zgłosił żądanie alokacji.</span><span class="sxs-lookup"><span data-stu-id="d4020-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="d4020-109">Jeśli nie można przydzielić pamięci, środowisko CLR nie gwarantuje, że domena jest nadal można używać.</span><span class="sxs-lookup"><span data-stu-id="d4020-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="d4020-110">Host decyduje, jaką akcję do wykonania w przypadku alokacja nie mogą zostać spełnione.</span><span class="sxs-lookup"><span data-stu-id="d4020-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="d4020-111">Można nakazać, środowisko CLR, aby przerwać `AppDomain` automatycznie, lub zezwolenia na jego pozostanie uruchomione przez wywołanie metody w [iclrpolicymanager —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d4020-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="d4020-112">Wskazuje, że przydział ma kluczowe znaczenie dla wykonywania kodu zarządzanego w procesie.</span><span class="sxs-lookup"><span data-stu-id="d4020-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="d4020-113">Ta wartość jest używana podczas uruchamiania i podczas uruchamiania finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="d4020-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="d4020-114">Jeśli nie można przydzielić pamięci, środowisko CLR nie może działać w procesie.</span><span class="sxs-lookup"><span data-stu-id="d4020-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="d4020-115">Jeśli alokacja nie powiedzie się, środowisko CLR skutecznie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="d4020-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="d4020-116">Wszystkie kolejne wywołania do środowiska CLR zakończona niepowodzeniem z HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d4020-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="d4020-117">Wskazuje przydział mają kluczowe znaczenie dla uruchomienia zadania, który zgłosił żądanie alokacji.</span><span class="sxs-lookup"><span data-stu-id="d4020-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="d4020-118">Jeśli nie można przydzielić pamięci, środowisko CLR nie gwarantuje zadania mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="d4020-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="d4020-119">W przypadku awarii, środowisko CLR wywołuje <xref:System.Threading.ThreadAbortException> w wątku systemu fizycznego operacji.</span><span class="sxs-lookup"><span data-stu-id="d4020-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4020-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4020-120">Remarks</span></span>  
 <span data-ttu-id="d4020-121">Metody alokacji pamięci, które są zdefiniowane w [ihostmemorymanager —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) i [ihostmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfejsów przyjmować parametr tego typu.</span><span class="sxs-lookup"><span data-stu-id="d4020-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="d4020-122">W zależności od ważności awarii hosta można zdecydować, czy natychmiast zwraca Niepowodzenie żądania alokacji lub poczekaj, aż mogą zostać zrealizowane.</span><span class="sxs-lookup"><span data-stu-id="d4020-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4020-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4020-123">Requirements</span></span>  
 <span data-ttu-id="d4020-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4020-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4020-125">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4020-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4020-126">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4020-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4020-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4020-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4020-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4020-128">See also</span></span>

- [<span data-ttu-id="d4020-129">ICLRMemoryNotificationCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4020-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="d4020-130">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d4020-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
