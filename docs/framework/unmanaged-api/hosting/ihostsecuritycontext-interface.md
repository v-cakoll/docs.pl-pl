---
title: IHostSecurityContext — Interfejs
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d71b7e1265110a70329377ce8ab7430e1943c49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124036"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="9a7e6-102">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9a7e6-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="9a7e6-103">Umożliwia środowisko uruchomieniowe języka wspólnego (CLR), aby zachować informacje kontekstu zabezpieczeń implementowany przez hosta.</span><span class="sxs-lookup"><span data-stu-id="9a7e6-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a7e6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9a7e6-104">Methods</span></span>  
  
|<span data-ttu-id="9a7e6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a7e6-105">Method</span></span>|<span data-ttu-id="9a7e6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9a7e6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a7e6-107">Capture, metoda</span><span class="sxs-lookup"><span data-stu-id="9a7e6-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="9a7e6-108">Pobiera klon `IHostSecurityContext` wystąpienia zwrócony z wywołania do [ihostsecuritymanager::getsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="9a7e6-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a7e6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a7e6-109">Remarks</span></span>  
 <span data-ttu-id="9a7e6-110">Hosta można kontrolować wszelki dostęp kodu do tokenów wątku przez kod CLR i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9a7e6-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="9a7e6-111">Można to także zapewnić pełne zabezpieczenia informacji kontekstowych jest przekazywany w operacji asynchronicznych lub punkty kodowe dostęp ograniczony kod.</span><span class="sxs-lookup"><span data-stu-id="9a7e6-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> `IHostSecurityContext` <span data-ttu-id="9a7e6-112">hermetyzuje informacje kontekstu zabezpieczeń, która jest nieprzezroczysta dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9a7e6-112">encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="9a7e6-113">Środowisko uruchomieniowe rejestruje te informacje przy użyciu `Capture`, i przeniesieniu jej wątek puli procesów roboczych elementu wysyłania, finalizator wykonania i moduł i klasy konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="9a7e6-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a7e6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a7e6-114">Requirements</span></span>  
 <span data-ttu-id="9a7e6-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a7e6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a7e6-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a7e6-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a7e6-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a7e6-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9a7e6-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9a7e6-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a7e6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a7e6-119">See also</span></span>

- [<span data-ttu-id="9a7e6-120">ICLRHostProtectionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9a7e6-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="9a7e6-121">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9a7e6-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="9a7e6-122">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="9a7e6-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
