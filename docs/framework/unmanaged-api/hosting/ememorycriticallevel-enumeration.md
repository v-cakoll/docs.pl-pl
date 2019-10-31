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
ms.openlocfilehash: 8364d38f7ab81b73fd8b47d2251bc0ff1b2c71e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138247"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="47a1f-102">EMemoryCriticalLevel — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="47a1f-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="47a1f-103">Zawiera wartości wskazujące wpływ błędu w przypadku żądania określonego przydziału pamięci, ale nie można go spełnić.</span><span class="sxs-lookup"><span data-stu-id="47a1f-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47a1f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="47a1f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="47a1f-105">Members</span></span>  
  
|<span data-ttu-id="47a1f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="47a1f-106">Member</span></span>|<span data-ttu-id="47a1f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="47a1f-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="47a1f-108">Wskazuje, że alokacja ma kluczowe znaczenie dla wykonywania kodu zarządzanego w domenie, która zażądała alokacji.</span><span class="sxs-lookup"><span data-stu-id="47a1f-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="47a1f-109">Jeśli nie można przydzielić pamięci, środowisko CLR nie może zagwarantować, że domena nadal będzie można używać.</span><span class="sxs-lookup"><span data-stu-id="47a1f-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="47a1f-110">Host decyduje, jakie działania należy podjąć, gdy nie można spełnić alokacji.</span><span class="sxs-lookup"><span data-stu-id="47a1f-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="47a1f-111">Może nakazać, aby środowisko CLR przerywał `AppDomain` automatycznie, lub zezwolić na działanie przez wywoływanie metod w [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="47a1f-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="47a1f-112">Wskazuje, że alokacja ma krytyczne znaczenie dla wykonywania kodu zarządzanego w procesie.</span><span class="sxs-lookup"><span data-stu-id="47a1f-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="47a1f-113">Ta wartość jest używana podczas uruchamiania i uruchamiania finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="47a1f-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="47a1f-114">Jeśli nie można przydzielić pamięci, środowisko CLR nie może działać w procesie.</span><span class="sxs-lookup"><span data-stu-id="47a1f-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="47a1f-115">Jeśli alokacja nie powiedzie się, środowisko CLR jest skutecznie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="47a1f-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="47a1f-116">Wszystkie kolejne wywołania środowiska CLR kończą się niepowodzeniem z HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="47a1f-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="47a1f-117">Wskazuje, że alokacja ma krytyczne znaczenie dla uruchomienia zadania, które zażądało alokacji.</span><span class="sxs-lookup"><span data-stu-id="47a1f-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="47a1f-118">Jeśli nie można przydzielić pamięci, środowisko CLR nie gwarantuje, że zadanie może być wykonane.</span><span class="sxs-lookup"><span data-stu-id="47a1f-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="47a1f-119">W przypadku awarii środowisko CLR wywołuje <xref:System.Threading.ThreadAbortException> w wątku fizycznego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="47a1f-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47a1f-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47a1f-120">Remarks</span></span>  
 <span data-ttu-id="47a1f-121">Metody alokacji pamięci zdefiniowane w interfejsach [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) i [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) przyjmują parametr tego typu.</span><span class="sxs-lookup"><span data-stu-id="47a1f-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="47a1f-122">W zależności od wagi błędu host może zdecydować, czy natychmiast przerwać żądanie alokacji, czy czekać, aż będzie można je spełnić.</span><span class="sxs-lookup"><span data-stu-id="47a1f-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a1f-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47a1f-123">Requirements</span></span>  
 <span data-ttu-id="47a1f-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47a1f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47a1f-125">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="47a1f-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47a1f-126">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="47a1f-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47a1f-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47a1f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a1f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47a1f-128">See also</span></span>

- [<span data-ttu-id="47a1f-129">ICLRMemoryNotificationCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="47a1f-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="47a1f-130">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="47a1f-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
