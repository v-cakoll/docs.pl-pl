---
title: ICLRControl — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615842"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="b2caa-102">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b2caa-102">ICLRControl Interface</span></span>
<span data-ttu-id="b2caa-103">Dostarcza metody, które umożliwiają hostowi uzyskanie odwołań do i Konfigurowanie aspektów środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b2caa-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2caa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b2caa-104">Methods</span></span>  
  
|<span data-ttu-id="b2caa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2caa-105">Method</span></span>|<span data-ttu-id="b2caa-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b2caa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2caa-107">GetCLRManager, metoda</span><span class="sxs-lookup"><span data-stu-id="b2caa-107">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="b2caa-108">Pobiera wskaźnik interfejsu do wystąpienia dowolnego typu Menedżera, którego host może użyć do skonfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b2caa-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="b2caa-109">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="b2caa-109">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="b2caa-110">Ustawia typ pochodzący od <xref:System.AppDomainManager> typu dla menedżerów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2caa-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2caa-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2caa-111">Requirements</span></span>  
 <span data-ttu-id="b2caa-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2caa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2caa-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b2caa-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2caa-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b2caa-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2caa-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2caa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2caa-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2caa-116">See also</span></span>

- [<span data-ttu-id="b2caa-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2caa-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b2caa-118">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2caa-118">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="b2caa-119">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2caa-119">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="b2caa-120">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2caa-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="b2caa-121">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2caa-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="b2caa-122">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2caa-122">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="b2caa-123">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2caa-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="b2caa-124">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2caa-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="b2caa-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b2caa-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
