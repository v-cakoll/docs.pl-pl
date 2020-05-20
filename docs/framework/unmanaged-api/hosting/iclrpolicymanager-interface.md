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
ms.openlocfilehash: 631301a10aee96bb00aeda6b0b8695f0aea186a8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703475"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="f2d86-102">ICLRPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f2d86-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="f2d86-103">Dostarcza metody, które pozwalają hostowi określić akcje zasad, które mają być podejmowane w przypadku awarii i przekroczeń limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="f2d86-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2d86-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f2d86-104">Methods</span></span>  
  
|<span data-ttu-id="f2d86-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f2d86-105">Method</span></span>|<span data-ttu-id="f2d86-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f2d86-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2d86-107">SetActionOnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="f2d86-107">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="f2d86-108">Określa akcję zasad, która ma być wykonywana przez środowisko uruchomieniowe języka wspólnego (CLR) w przypadku wystąpienia określonego błędu.</span><span class="sxs-lookup"><span data-stu-id="f2d86-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="f2d86-109">SetActionOnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="f2d86-109">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="f2d86-110">Określa akcję zasad wykonywaną przez środowisko CLR po przełączeniu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="f2d86-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="f2d86-111">SetDefaultAction, metoda</span><span class="sxs-lookup"><span data-stu-id="f2d86-111">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="f2d86-112">Określa akcję zasad wykonywaną przez środowisko CLR po wystąpieniu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="f2d86-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="f2d86-113">SetTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="f2d86-113">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="f2d86-114">Ustawia wartość limitu czasu dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="f2d86-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="f2d86-115">SetTimeoutAndAction, metoda</span><span class="sxs-lookup"><span data-stu-id="f2d86-115">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="f2d86-116">Ustawia wartość limitu czasu dla określonej operacji i określa akcję zasad, którą powinien wykonać środowisko CLR po wystąpieniu operacji.</span><span class="sxs-lookup"><span data-stu-id="f2d86-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="f2d86-117">SetUnhandledExceptionPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="f2d86-117">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="f2d86-118">Określa zachowanie środowiska CLR w przypadku wystąpienia nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f2d86-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2d86-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2d86-119">Requirements</span></span>  
 <span data-ttu-id="f2d86-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2d86-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2d86-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f2d86-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2d86-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f2d86-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2d86-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2d86-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d86-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2d86-124">See also</span></span>

- [<span data-ttu-id="f2d86-125">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f2d86-125">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="f2d86-126">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f2d86-126">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="f2d86-127">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f2d86-127">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="f2d86-128">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f2d86-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
