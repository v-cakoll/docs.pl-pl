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
ms.openlocfilehash: fa2b5052a1d569487f0c6c72699ff9ab571beefc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504397"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="97510-102">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="97510-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="97510-103">Opisuje zestaw błędów, dla których host może ustawiać akcje zasad.</span><span class="sxs-lookup"><span data-stu-id="97510-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97510-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97510-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="97510-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="97510-105">Members</span></span>  
  
|<span data-ttu-id="97510-106">Członek</span><span class="sxs-lookup"><span data-stu-id="97510-106">Member</span></span>|<span data-ttu-id="97510-107">Opis</span><span class="sxs-lookup"><span data-stu-id="97510-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="97510-108">Wystąpił błąd podczas próby przydzielenia zasobu (takiego jak wątek, blok pamięci lub blokada) w niekrytycznym regionie kodu.</span><span class="sxs-lookup"><span data-stu-id="97510-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="97510-109">Wystąpił błąd podczas próby przydzielenia zasobu (takiego jak wątek, blok pamięci lub blokada) w krytycznym regionie kodu.</span><span class="sxs-lookup"><span data-stu-id="97510-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="97510-110">Środowisko uruchomieniowe języka wspólnego (CLR) nie może już uruchamiać kodu zarządzanego w procesie.</span><span class="sxs-lookup"><span data-stu-id="97510-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="97510-111">Odtąd wywołania funkcji hostingu zwracają wartość HRESULT HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="97510-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="97510-112">Wątek nie może zwolnić blokady po powrocie z <xref:System.AppDomain> obiektu.</span><span class="sxs-lookup"><span data-stu-id="97510-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="97510-113">Host nie może ustawić tego błędu, aby powodował przerwanie wątku.</span><span class="sxs-lookup"><span data-stu-id="97510-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="97510-114">Nastąpiło przepełnienie stosu.</span><span class="sxs-lookup"><span data-stu-id="97510-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="97510-115">Podjęto próbę odczytu lub zapisu chronionej pamięci.</span><span class="sxs-lookup"><span data-stu-id="97510-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="97510-116">Nieobsługiwane w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="97510-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="97510-117">Wystąpił błąd kontraktu kodu.</span><span class="sxs-lookup"><span data-stu-id="97510-117">A code contract failure occurred.</span></span> <span data-ttu-id="97510-118">Zobacz [kontrakty kodu](../../debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="97510-118">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97510-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97510-119">Remarks</span></span>  
 <span data-ttu-id="97510-120">Zobacz metodę [ICLRPolicyManager:: SetActionOnFailure —](iclrpolicymanager-setactiononfailure-method.md) , aby uzyskać listę wartości [EPolicyAction —](epolicyaction-enumeration.md) , których host może użyć do określenia akcji zasad dla warunków niepowodzeń.</span><span class="sxs-lookup"><span data-stu-id="97510-120">See the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="97510-121">Aby uzyskać więcej informacji na temat krytycznych i niekrytycznych regionów kodu, zobacz [EClrOperation —](eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="97510-121">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97510-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97510-122">Requirements</span></span>  
 <span data-ttu-id="97510-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97510-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97510-124">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="97510-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97510-125">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="97510-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97510-126">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97510-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97510-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97510-127">See also</span></span>

- [<span data-ttu-id="97510-128">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="97510-128">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="97510-129">SetActionOnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="97510-129">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="97510-130">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="97510-130">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="97510-131">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="97510-131">Hosting Enumerations</span></span>](hosting-enumerations.md)
