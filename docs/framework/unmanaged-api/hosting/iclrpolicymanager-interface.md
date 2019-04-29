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
ms.openlocfilehash: 2eeccc4dfd7a7147fe791444eeeca2bd3a844305
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638869"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="06ff6-102">ICLRPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="06ff6-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="06ff6-103">Udostępnia metody, które umożliwiają hosta określić zasady działań podejmowanych w przypadku awarii lub przekroczenia limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="06ff6-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06ff6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="06ff6-104">Methods</span></span>  
  
|<span data-ttu-id="06ff6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="06ff6-105">Method</span></span>|<span data-ttu-id="06ff6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="06ff6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06ff6-107">SetActionOnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="06ff6-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="06ff6-108">Określa akcję zasad, których środowisko uruchomieniowe języka wspólnego (CLR) powinna wykonać, gdy wystąpi awaria określonej.</span><span class="sxs-lookup"><span data-stu-id="06ff6-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="06ff6-109">SetActionOnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="06ff6-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="06ff6-110">Określa akcję zasady, którą środowisko CLR powinna wykonać, gdy upłynie limit czasu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="06ff6-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="06ff6-111">SetDefaultAction, metoda</span><span class="sxs-lookup"><span data-stu-id="06ff6-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="06ff6-112">Określa akcję zasady, którą środowisko CLR powinna wykonać, gdy występuje określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="06ff6-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="06ff6-113">SetTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="06ff6-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="06ff6-114">Ustawia wartość limitu czasu dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="06ff6-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="06ff6-115">SetTimeoutAndAction, metoda</span><span class="sxs-lookup"><span data-stu-id="06ff6-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="06ff6-116">Ustawia wartość limitu czasu dla określonej operacji i określa akcję zasady, którą środowisko CLR powinna wykonać, gdy operacja jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="06ff6-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="06ff6-117">SetUnhandledExceptionPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="06ff6-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="06ff6-118">Określa zachowanie środowiska CLR, po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="06ff6-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06ff6-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06ff6-119">Requirements</span></span>  
 <span data-ttu-id="06ff6-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06ff6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06ff6-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="06ff6-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="06ff6-122">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06ff6-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06ff6-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06ff6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ff6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06ff6-124">See also</span></span>

- [<span data-ttu-id="06ff6-125">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="06ff6-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="06ff6-126">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="06ff6-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="06ff6-127">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="06ff6-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="06ff6-128">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="06ff6-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
