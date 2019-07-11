---
title: EClrFailure — Wyliczenie
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f3e39d94996f14f1ae6593b9adaa5db3ef674c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769652"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="e8f21-102">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e8f21-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="e8f21-103">W tym artykule opisano zestaw awarie, dla których hosta można ustawić akcje dotyczące zasad.</span><span class="sxs-lookup"><span data-stu-id="e8f21-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f21-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8f21-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="e8f21-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e8f21-105">Members</span></span>  
  
|<span data-ttu-id="e8f21-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e8f21-106">Member</span></span>|<span data-ttu-id="e8f21-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e8f21-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="e8f21-108">Wystąpił błąd podczas próby przydzielenia zasobu (na przykład wątku, blok pamięci lub blokadę) w regionie niekrytyczne kodu.</span><span class="sxs-lookup"><span data-stu-id="e8f21-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="e8f21-109">Wystąpił błąd podczas próby przydzielenia zasobu (na przykład wątku, blok pamięci lub blokady) krytyczne obszar kodu.</span><span class="sxs-lookup"><span data-stu-id="e8f21-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="e8f21-110">Środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do uruchomienia kodu zarządzanego w procesie.</span><span class="sxs-lookup"><span data-stu-id="e8f21-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="e8f21-111">Odtąd wywołania wszystkie funkcje hostingu zwraca wartość HRESULT HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8f21-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="e8f21-112">Wątek nie udało się zwolnić blokady po powrocie z <xref:System.AppDomain> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e8f21-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="e8f21-113">Host nie można ustawić tego błędu, aby spowodować, że wątek przerwać.</span><span class="sxs-lookup"><span data-stu-id="e8f21-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="e8f21-114">Wystąpiło przepełnienie stosu.</span><span class="sxs-lookup"><span data-stu-id="e8f21-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="e8f21-115">Nastąpiła próba odczytu lub zapisu pamięci chronionej.</span><span class="sxs-lookup"><span data-stu-id="e8f21-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="e8f21-116">Nie są obsługiwane w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e8f21-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="e8f21-117">Wystąpił błąd kodu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e8f21-117">A code contract failure occurred.</span></span> <span data-ttu-id="e8f21-118">Zobacz [kodu umów](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e8f21-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8f21-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8f21-119">Remarks</span></span>  
 <span data-ttu-id="e8f21-120">Zobacz [iclrpolicymanager::setactiononfailure —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metody, aby uzyskać listę [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości hosta można użyć do określenia akcje zasad warunki błędu.</span><span class="sxs-lookup"><span data-stu-id="e8f21-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="e8f21-121">Aby uzyskać więcej informacji na temat regionów krytyczne i niekrytyczne kodu, zobacz [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e8f21-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8f21-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8f21-122">Requirements</span></span>  
 <span data-ttu-id="e8f21-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8f21-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8f21-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8f21-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8f21-125">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8f21-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8f21-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8f21-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f21-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8f21-127">See also</span></span>

- [<span data-ttu-id="e8f21-128">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8f21-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="e8f21-129">SetActionOnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="e8f21-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="e8f21-130">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8f21-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="e8f21-131">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e8f21-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
