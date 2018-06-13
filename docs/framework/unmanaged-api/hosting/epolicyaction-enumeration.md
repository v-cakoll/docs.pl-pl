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
ms.openlocfilehash: 14908ae641c8539659e6014deb2c5f35a6d1cfbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433633"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="a5522-102">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a5522-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="a5522-103">Opisuje akcje podejmowane zasad hosta można ustawić dla operacji opisanego przez [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) i błędów opisanego przez [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a5522-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5522-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5522-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a5522-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a5522-105">Members</span></span>  
  
|<span data-ttu-id="a5522-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a5522-106">Member</span></span>|<span data-ttu-id="a5522-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a5522-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="a5522-108">Określa, że środowisko uruchomieniowe języka wspólnego (CLR) należy przerwać wątek bezpiecznie.</span><span class="sxs-lookup"><span data-stu-id="a5522-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="a5522-109">Bezpieczne przerwania obejmuje próbuje uruchomić wszystkie `finally` blokuje żadnego `catch` bloki związanych z wątku przerwań i finalizatory.</span><span class="sxs-lookup"><span data-stu-id="a5522-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="a5522-110">Określa, czy CLR należy wprowadzić w stanie wyłączenia.</span><span class="sxs-lookup"><span data-stu-id="a5522-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="a5522-111">Żadne dodatkowe zarządzanego kodu mogą być wykonywane w procesie dotyczy i wątków jest blokowane wprowadzeniu do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a5522-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="a5522-112">Określa, że środowisko CLR powinien podejmować próbę łagodne zakończenia procesu, w tym systemem finalizatory i oczyszczania i operacji rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="a5522-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="a5522-113">Określa środowisko CLR powinien natychmiast zakończyć proces bez przeprowadzania finalizatory lub oczyszczania i operacji rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="a5522-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="a5522-114">Nowever, powiadomienie jest wysyłane do debugera.</span><span class="sxs-lookup"><span data-stu-id="a5522-114">Nowever, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="a5522-115">Określa, że wykonywane żadne działania.</span><span class="sxs-lookup"><span data-stu-id="a5522-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="a5522-116">Określa, że środowisko CLR powinna wykonuje przerwania niegrzeczny wątku.</span><span class="sxs-lookup"><span data-stu-id="a5522-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="a5522-117">Tylko te `catch` i `finally` oznaczonej jako bloki <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="a5522-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="a5522-118">Określa środowisko CLR powinna zakończyć proces bez przeprowadzania finalizatory lub rejestrowania operacji.</span><span class="sxs-lookup"><span data-stu-id="a5522-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="a5522-119">Określa, że niegrzeczny zwolnienie powinno być wykonywane przez środowisko CLR <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a5522-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="a5522-120">Finalizatory tylko oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="a5522-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="a5522-121">Podobnie, wszystkie wątki z tym <xref:System.AppDomain> ich stosu odbierania `ThreadAbortException`, ale tylko te `catch` i `finally` oznaczonej jako bloki <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="a5522-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="a5522-122">Określa, że jest zgłaszany wyjątek odpowiednie do warunku, takich jak braku pamięci, przepełnienie buforu i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="a5522-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="a5522-123">Określa, że <xref:System.AppDomain> powinny zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="a5522-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="a5522-124">Środowisko CLR podejmie próbę uruchomienia finalizatory.</span><span class="sxs-lookup"><span data-stu-id="a5522-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5522-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5522-125">Remarks</span></span>  
 <span data-ttu-id="a5522-126">Host ustawia akcje zasady przez wywołanie metody [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a5522-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="a5522-127">Uzyskać informacji o niegrzeczny i bezpieczne przerwań, zobacz [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a5522-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5522-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5522-128">Requirements</span></span>  
 <span data-ttu-id="a5522-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5522-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5522-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a5522-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5522-131">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5522-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5522-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5522-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5522-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5522-133">See Also</span></span>  
 [<span data-ttu-id="a5522-134">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a5522-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="a5522-135">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5522-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="a5522-136">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5522-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="a5522-137">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a5522-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
