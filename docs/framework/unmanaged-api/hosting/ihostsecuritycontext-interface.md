---
title: "IHostSecurityContext — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityContext
helpviewer_keywords: IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ee464e47ad6e333b507c199e1857309f640a37b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="d5f6e-102">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d5f6e-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="d5f6e-103">Umożliwia środowisko uruchomieniowe języka wspólnego (CLR), aby zachować informacje kontekstu zabezpieczeń zaimplementowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="d5f6e-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5f6e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d5f6e-104">Methods</span></span>  
  
|<span data-ttu-id="d5f6e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d5f6e-105">Method</span></span>|<span data-ttu-id="d5f6e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d5f6e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5f6e-107">Capture, metoda</span><span class="sxs-lookup"><span data-stu-id="d5f6e-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="d5f6e-108">Pobiera Sklonowanie `IHostSecurityContext` wystąpienia zwrócone w wyniku wywołania [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="d5f6e-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5f6e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5f6e-109">Remarks</span></span>  
 <span data-ttu-id="d5f6e-110">Hosta można kontrolować kod dostęp do tokenów wątku przez kod zarówno CLR, jak i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d5f6e-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="d5f6e-111">Zapewnia również Zabezpieczenia pełne informacje o kontekście jest przekazywany przez operacje asynchroniczne lub punktów kodowych z ograniczeniami kod dostępu.</span><span class="sxs-lookup"><span data-stu-id="d5f6e-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="d5f6e-112">`IHostSecurityContext`hermetyzuje informacje kontekstu zabezpieczeń, które jest nieprzezroczysta dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d5f6e-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="d5f6e-113">Środowisko uruchomieniowe przechwytuje te informacje przy użyciu `Capture`, i przenosi ją wysyłania elementu roboczego puli wątków, wykonanie finalizatora i konstruktory moduł i klasy.</span><span class="sxs-lookup"><span data-stu-id="d5f6e-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5f6e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5f6e-114">Requirements</span></span>  
 <span data-ttu-id="d5f6e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5f6e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5f6e-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5f6e-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5f6e-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5f6e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5f6e-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5f6e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5f6e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5f6e-119">See Also</span></span>  
 [<span data-ttu-id="d5f6e-120">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5f6e-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="d5f6e-121">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5f6e-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="d5f6e-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d5f6e-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
