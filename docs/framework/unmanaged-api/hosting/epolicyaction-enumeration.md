---
title: EPolicyAction — Wyliczenie
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75bd7da67cbac958f0b34c8295454a719962c7ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628720"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="8e442-102">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8e442-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="8e442-103">W tym artykule opisano akcje zasad hosta można ustawić dla operacji opisanych przez [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) i awarie opisanego przez [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8e442-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e442-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e442-104">Syntax</span></span>  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="8e442-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8e442-105">Members</span></span>  
  
|<span data-ttu-id="8e442-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8e442-106">Member</span></span>|<span data-ttu-id="8e442-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8e442-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="8e442-108">Określa, że środowisko uruchomieniowe języka wspólnego (CLR) należy przerwać bez problemu zmieniała wątku.</span><span class="sxs-lookup"><span data-stu-id="8e442-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="8e442-109">Łagodne przerwania obejmuje próbuje uruchomić wszystkie `finally` blokach dowolny `catch` bloków związanych z wątku przerwań i finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="8e442-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="8e442-110">Określa, że środowisko CLR należy wprowadzić w stanie wyłączenia.</span><span class="sxs-lookup"><span data-stu-id="8e442-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="8e442-111">Żadne dodatkowe zarządzanego kodu mogą być wykonywane w procesie zainfekowanego i możliwość wprowadzania środowiska CLR są blokowane wątki.</span><span class="sxs-lookup"><span data-stu-id="8e442-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="8e442-112">Określa, że środowisko CLR powinien podejmować próbę Łagodne wyjście procesu, łącznie z systemem finalizatory i oczyszczania i operacji rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="8e442-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="8e442-113">Określa środowisko CLR powinien natychmiast zakończyć proces bez uruchamiania finalizatory i oczyszczania i operacji rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="8e442-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="8e442-114">Jednak powiadomienie jest wysyłane do debugera.</span><span class="sxs-lookup"><span data-stu-id="8e442-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="8e442-115">Określa, czy podjęta żadna akcja.</span><span class="sxs-lookup"><span data-stu-id="8e442-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="8e442-116">Określa, że przerwanie wątku prosta powinno być wykonywane przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="8e442-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="8e442-117">Tylko te `catch` i `finally` bloki oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="8e442-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="8e442-118">Określa środowisko CLR powinna zakończyć proces bez uruchamiania finalizatory i rejestrowanie operacji.</span><span class="sxs-lookup"><span data-stu-id="8e442-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="8e442-119">Określa, że prosta zwolnienie powinno być wykonywane przez środowisko CLR <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8e442-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="8e442-120">Finalizatory tylko oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="8e442-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="8e442-121">Podobnie wszystkie wątki w tym <xref:System.AppDomain> w stosie ich odbierania `ThreadAbortException`, a jedynie tych `catch` i `finally` bloki oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="8e442-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="8e442-122">Określa, że odpowiednie do warunku, takie jak braku pamięci, przepełnienie buforu i tak dalej, należy zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8e442-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="8e442-123">Określa, że <xref:System.AppDomain> powinny zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="8e442-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="8e442-124">Środowisko CLR podejmie próbę uruchomienia finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="8e442-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e442-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e442-125">Remarks</span></span>  
 <span data-ttu-id="8e442-126">Host ustawia akcje zasad przez wywołanie metody [iclrpolicymanager —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8e442-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="8e442-127">Aby o prosta i płynnego przerwań, zobacz [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8e442-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e442-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e442-128">Requirements</span></span>  
 <span data-ttu-id="8e442-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e442-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e442-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8e442-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e442-131">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e442-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e442-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e442-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e442-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e442-133">See also</span></span>

- [<span data-ttu-id="8e442-134">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8e442-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="8e442-135">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e442-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="8e442-136">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e442-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="8e442-137">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8e442-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
