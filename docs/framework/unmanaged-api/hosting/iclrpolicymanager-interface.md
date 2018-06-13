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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e8a1b1bcf4470f5e754775b1137b8221ae1d0b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435150"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="651b2-102">ICLRPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="651b2-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="651b2-103">Udostępnia metody, które umożliwiają hosta określić zasady akcje do wykonania w przypadku awarii i przekroczeń limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="651b2-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="651b2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="651b2-104">Methods</span></span>  
  
|<span data-ttu-id="651b2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="651b2-105">Method</span></span>|<span data-ttu-id="651b2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="651b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="651b2-107">SetActionOnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="651b2-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="651b2-108">Określa akcję zasady, którą powinno mieć środowisko uruchomieniowe języka wspólnego (CLR), gdy wystąpi określony błąd.</span><span class="sxs-lookup"><span data-stu-id="651b2-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="651b2-109">SetActionOnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="651b2-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="651b2-110">Określa akcję zasad, które CLR powinien wykonać, gdy upłynie limit czasu operacji określony.</span><span class="sxs-lookup"><span data-stu-id="651b2-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="651b2-111">SetDefaultAction, metoda</span><span class="sxs-lookup"><span data-stu-id="651b2-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="651b2-112">Określa akcję zasad CLR powinien zająć po wystąpieniu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="651b2-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="651b2-113">SetTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="651b2-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="651b2-114">Ustawia wartość limitu czasu dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="651b2-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="651b2-115">SetTimeoutAndAction, metoda</span><span class="sxs-lookup"><span data-stu-id="651b2-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="651b2-116">Ustawia wartość limitu czasu dla określonej operacji, a następnie określa akcję zasad CLR powinien zająć podczas operacji.</span><span class="sxs-lookup"><span data-stu-id="651b2-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="651b2-117">SetUnhandledExceptionPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="651b2-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="651b2-118">Określa zachowanie środowiska CLR, gdy wystąpi nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="651b2-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="651b2-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="651b2-119">Requirements</span></span>  
 <span data-ttu-id="651b2-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="651b2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="651b2-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="651b2-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="651b2-122">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="651b2-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="651b2-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="651b2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="651b2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="651b2-124">See Also</span></span>  
 [<span data-ttu-id="651b2-125">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="651b2-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="651b2-126">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="651b2-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="651b2-127">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="651b2-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="651b2-128">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="651b2-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
