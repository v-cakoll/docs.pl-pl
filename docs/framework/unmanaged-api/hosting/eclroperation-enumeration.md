---
title: EClrOperation — Wyliczenie
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
ms.openlocfilehash: e7cb1c2070e760258e548d2f45e3b6ed11e046c4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616323"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="0f9d1-102">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0f9d1-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="0f9d1-103">Opisuje zestaw operacji, dla których host może stosować akcje zasad.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f9d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f9d1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="0f9d1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0f9d1-105">Members</span></span>  
  
|<span data-ttu-id="0f9d1-106">Członek</span><span class="sxs-lookup"><span data-stu-id="0f9d1-106">Member</span></span>|<span data-ttu-id="0f9d1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0f9d1-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="0f9d1-108">Host może określać akcje zasad, które mają zostać podjęte, gdy <xref:System.AppDomain> zostanie zwolniony w sposób niebezpieczny (prosta).</span><span class="sxs-lookup"><span data-stu-id="0f9d1-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="0f9d1-109">Host może określać akcje zasad, które mają zostać wykonane po <xref:System.AppDomain> zakończeniu ładowania.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="0f9d1-110">Host może określać akcje zasad, które mają być podejmowane po uruchomieniu finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="0f9d1-111">Host może określić akcje zasad, które mają zostać wykonane po zakończeniu procesu.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="0f9d1-112">Host może określać akcje zasad, które mają być podejmowane w przypadku przerwania wątku.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="0f9d1-113">Host może określać akcje zasad, które mają być podejmowane w przypadku przerwania wątku prosta w krytycznym regionie kodu.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="0f9d1-114">Host może określać akcje zasad, które mają być podejmowane po przerwaniu wątku prosta w niekrytycznym regionie kodu.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f9d1-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f9d1-115">Remarks</span></span>  
 <span data-ttu-id="0f9d1-116">Infrastruktura niezawodności aparatu plików wykonywalnych języka wspólnego (CLR) odróżnia między przerwami a błędami alokacji zasobów, które występują w krytycznych regionach kodu i tych, które występują w niekrytycznych regionach kodu.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="0f9d1-117">Ta różnica została zaprojektowana tak, aby umożliwić hostom Ustawianie różnych zasad w zależności od tego, gdzie wystąpi błąd w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="0f9d1-118">*Krytyczny region kodu* jest dowolnym miejscem, w którym środowisko CLR nie może zagwarantować, że przerywanie zadania lub niepowodzenie żądania dla zasobów będzie wpływać tylko na bieżące zadanie.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="0f9d1-119">Na przykład, jeśli zadanie utrzymuje blokadę i otrzymuje wynik HRESULT wskazujący błąd podczas tworzenia żądania alokacji pamięci, to nie wystarczy po prostu przerwać to zadanie, aby zapewnić stabilność <xref:System.AppDomain> , ponieważ <xref:System.AppDomain> może zawierać inne zadania oczekujące na tę samą blokadę.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="0f9d1-120">Aby porzucić bieżące zadanie, może spowodować, że te inne zadania przestaną odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-120">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="0f9d1-121">W takim przypadku host musi mieć możliwość zwolnienia całości, <xref:System.AppDomain> a nie ryzyka potencjalnej niestabilności.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="0f9d1-122">*Niekrytyczny region kodu*, z drugiej strony, to region, w którym środowisko CLR może zagwarantować, że przerwanie lub awaria będzie wpływać tylko na zadanie, na którym wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="0f9d1-123">Środowisko CLR rozróżnia również łagodne i niebezpieczne przerwania (prosta).</span><span class="sxs-lookup"><span data-stu-id="0f9d1-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="0f9d1-124">Ogólnie rzecz biorąc, normalne lub bezpieczne przerwanie podejmuje wszelkie wysiłki, aby uruchomić procedury obsługi wyjątków i finalizatory przed przerwaniem zadania, podczas gdy przerwanie prosta nie daje takich gwarancji.</span><span class="sxs-lookup"><span data-stu-id="0f9d1-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f9d1-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f9d1-125">Requirements</span></span>  
 <span data-ttu-id="0f9d1-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f9d1-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f9d1-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f9d1-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f9d1-128">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0f9d1-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f9d1-129">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f9d1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9d1-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f9d1-130">See also</span></span>

- [<span data-ttu-id="0f9d1-131">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0f9d1-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="0f9d1-132">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0f9d1-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="0f9d1-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f9d1-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="0f9d1-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f9d1-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="0f9d1-135">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0f9d1-135">Hosting Enumerations</span></span>](hosting-enumerations.md)
