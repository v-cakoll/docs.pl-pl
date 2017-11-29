---
title: "EClrFailure — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrFailure
helpviewer_keywords: EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94358fd0626fa17f1fd6d3c365aff79f89dde467
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="a09e7-102">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a09e7-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="a09e7-103">W tym artykule opisano zestaw awarie, dla których hosta można ustawić akcje zasady.</span><span class="sxs-lookup"><span data-stu-id="a09e7-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a09e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a09e7-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="a09e7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a09e7-105">Members</span></span>  
  
|<span data-ttu-id="a09e7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a09e7-106">Member</span></span>|<span data-ttu-id="a09e7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a09e7-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="a09e7-108">Wystąpił błąd podczas próby przydzielić zasobów (np. wątek, blok pamięci lub blokady) w regionie niekrytyczne kodu.</span><span class="sxs-lookup"><span data-stu-id="a09e7-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="a09e7-109">Wystąpił błąd podczas próby przydzielić zasobów (np. wątek, blok pamięci lub blokady) w regionie krytyczne kodu.</span><span class="sxs-lookup"><span data-stu-id="a09e7-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="a09e7-110">Środowisko uruchomieniowe języka wspólnego (CLR) nie jest już mogli uruchamiać kodu zarządzanego w procesie.</span><span class="sxs-lookup"><span data-stu-id="a09e7-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="a09e7-111">Odtąd wartość HRESULT HOST_E_CLRNOTAVAILABLE zwracana wywołania wszystkie funkcje hostingu.</span><span class="sxs-lookup"><span data-stu-id="a09e7-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="a09e7-112">Wątek nie powiodło się zwolnić blokady na zwracanie z <xref:System.AppDomain> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a09e7-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="a09e7-113">Hosta nie można ustawić tego błędu powoduje wątku do przerwania.</span><span class="sxs-lookup"><span data-stu-id="a09e7-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="a09e7-114">Ma doszło do przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="a09e7-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="a09e7-115">Nastąpiła próba odczytu lub zapisu pamięci chronionej.</span><span class="sxs-lookup"><span data-stu-id="a09e7-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="a09e7-116">Nieobsługiwane w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a09e7-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="a09e7-117">Wystąpił błąd kontraktu kodu.</span><span class="sxs-lookup"><span data-stu-id="a09e7-117">A code contract failure occurred.</span></span> <span data-ttu-id="a09e7-118">Zobacz [kodu kontrakty](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a09e7-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a09e7-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a09e7-119">Remarks</span></span>  
 <span data-ttu-id="a09e7-120">Zobacz [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metody listę [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości hosta można użyć do określenia akcje zasad warunki błędu.</span><span class="sxs-lookup"><span data-stu-id="a09e7-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="a09e7-121">Aby uzyskać więcej informacji na temat regionów krytyczne i niekrytyczne kod, zobacz [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a09e7-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a09e7-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a09e7-122">Requirements</span></span>  
 <span data-ttu-id="a09e7-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a09e7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a09e7-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a09e7-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a09e7-125">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a09e7-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a09e7-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a09e7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09e7-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a09e7-127">See Also</span></span>  
 [<span data-ttu-id="a09e7-128">ICLRPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="a09e7-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="a09e7-129">SetActionOnFailure — metoda</span><span class="sxs-lookup"><span data-stu-id="a09e7-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [<span data-ttu-id="a09e7-130">IHostPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="a09e7-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="a09e7-131">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a09e7-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
