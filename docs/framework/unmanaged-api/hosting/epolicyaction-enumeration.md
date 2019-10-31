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
ms.openlocfilehash: eaba6b2166a82cfe825ffb98db515e24d4656462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138231"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="4ea7f-102">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4ea7f-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="4ea7f-103">Opisuje akcje zasad, które host może ustawić dla operacji opisanych przez [EClrOperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) i błędy opisane przez [EClrFailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4ea7f-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea7f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ea7f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="4ea7f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4ea7f-105">Members</span></span>  
  
|<span data-ttu-id="4ea7f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4ea7f-106">Member</span></span>|<span data-ttu-id="4ea7f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4ea7f-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="4ea7f-108">Określa, że środowisko uruchomieniowe języka wspólnego (CLR) powinno bezpiecznie przerwać wątek.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="4ea7f-109">Bezpieczne przerwanie obejmuje próby uruchomienia wszystkich bloków `finally`, wszelkich bloków `catch` związanych z przerwami wątku i finalizatorami.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="4ea7f-110">Określa, że środowisko CLR ma wejść w stan wyłączony.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="4ea7f-111">Żaden kod zarządzany nie może być wykonywany w odpowiednim procesie, a wątki są blokowane przed wprowadzeniem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="4ea7f-112">Określa, że środowisko CLR ma próbować bezpiecznie wyjść z procesu, w tym uruchamiania finalizatorów i wykonywania operacji czyszczenia i rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="4ea7f-113">Określa, że środowisko CLR powinno zakończyć proces natychmiast, bez uruchamiania finalizatorów lub wykonywania operacji czyszczenia i rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="4ea7f-114">Powiadomienia są jednak wysyłane do debugera.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="4ea7f-115">Określa, że żadna akcja nie powinna być wykonywana.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="4ea7f-116">Określa, że środowisko CLR ma wykonać przerwanie wątku prosta.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="4ea7f-117">Wykonywane są tylko te `catch` i bloki `finally` oznaczone jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="4ea7f-118">Określa, że środowisko CLR ma wyjść z procesu bez uruchamiania finalizatorów lub operacji rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="4ea7f-119">Określa, że środowisko CLR ma wykonać prosta Unload <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="4ea7f-120">Wykonywane są tylko finalizatory oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="4ea7f-121">Podobnie wszystkie wątki z tym <xref:System.AppDomain> w stosie odbierają `ThreadAbortException`, ale są wykonywane tylko te bloki `catch` i `finally` oznaczone jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="4ea7f-122">Określa, że wyjątek odpowiedni dla warunku, taki jak braku pamięci, przepełnienie buforu i tak dalej, powinien zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="4ea7f-123">Określa, że <xref:System.AppDomain> powinny być zwolnione.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="4ea7f-124">Środowisko CLR próbuje uruchomić finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="4ea7f-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ea7f-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ea7f-125">Remarks</span></span>  
 <span data-ttu-id="4ea7f-126">Host ustawia akcje zasad przez wywołanie metod interfejsu [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4ea7f-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="4ea7f-127">Aby uzyskać informacje na temat prosta i łagodnego przerwania, zobacz Wyliczenie [EClrOperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4ea7f-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ea7f-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ea7f-128">Requirements</span></span>  
 <span data-ttu-id="4ea7f-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ea7f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ea7f-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4ea7f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ea7f-131">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4ea7f-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ea7f-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ea7f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea7f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ea7f-133">See also</span></span>

- [<span data-ttu-id="4ea7f-134">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4ea7f-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="4ea7f-135">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ea7f-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="4ea7f-136">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ea7f-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="4ea7f-137">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4ea7f-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
