---
title: ICLRPolicyManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 59aa904d4c67326b60381d3476eaab179d7fa42b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140806"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="60994-102">ICLRPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="60994-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="60994-103">Dostarcza metody, które pozwalają hostowi określić akcje zasad, które mają być podejmowane w przypadku awarii i przekroczeń limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="60994-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60994-104">Metody</span><span class="sxs-lookup"><span data-stu-id="60994-104">Methods</span></span>  
  
|<span data-ttu-id="60994-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="60994-105">Method</span></span>|<span data-ttu-id="60994-106">Opis</span><span class="sxs-lookup"><span data-stu-id="60994-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60994-107">SetActionOnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="60994-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="60994-108">Określa akcję zasad, która ma być wykonywana przez środowisko uruchomieniowe języka wspólnego (CLR) w przypadku wystąpienia określonego błędu.</span><span class="sxs-lookup"><span data-stu-id="60994-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="60994-109">SetActionOnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="60994-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="60994-110">Określa akcję zasad wykonywaną przez środowisko CLR po przełączeniu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="60994-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="60994-111">SetDefaultAction, metoda</span><span class="sxs-lookup"><span data-stu-id="60994-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="60994-112">Określa akcję zasad wykonywaną przez środowisko CLR po wystąpieniu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="60994-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="60994-113">SetTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="60994-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="60994-114">Ustawia wartość limitu czasu dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="60994-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="60994-115">SetTimeoutAndAction, metoda</span><span class="sxs-lookup"><span data-stu-id="60994-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="60994-116">Ustawia wartość limitu czasu dla określonej operacji i określa akcję zasad, którą powinien wykonać środowisko CLR po wystąpieniu operacji.</span><span class="sxs-lookup"><span data-stu-id="60994-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="60994-117">SetUnhandledExceptionPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="60994-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="60994-118">Określa zachowanie środowiska CLR w przypadku wystąpienia nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="60994-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60994-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60994-119">Requirements</span></span>  
 <span data-ttu-id="60994-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60994-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60994-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="60994-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60994-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="60994-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60994-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60994-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60994-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60994-124">See also</span></span>

- [<span data-ttu-id="60994-125">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="60994-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="60994-126">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="60994-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="60994-127">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="60994-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="60994-128">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="60994-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
