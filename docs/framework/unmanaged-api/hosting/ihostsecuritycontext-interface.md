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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124036"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="9ee69-102">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9ee69-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="9ee69-103">Umożliwia środowisko uruchomieniowe języka wspólnego (CLR), aby zachować informacje kontekstu zabezpieczeń implementowany przez hosta.</span><span class="sxs-lookup"><span data-stu-id="9ee69-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ee69-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9ee69-104">Methods</span></span>  
  
|<span data-ttu-id="9ee69-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9ee69-105">Method</span></span>|<span data-ttu-id="9ee69-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9ee69-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ee69-107">Capture, metoda</span><span class="sxs-lookup"><span data-stu-id="9ee69-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="9ee69-108">Pobiera klon `IHostSecurityContext` wystąpienia zwrócony z wywołania do [ihostsecuritymanager::getsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="9ee69-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ee69-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ee69-109">Remarks</span></span>  
 <span data-ttu-id="9ee69-110">Hosta można kontrolować wszelki dostęp kodu do tokenów wątku przez kod CLR i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9ee69-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="9ee69-111">Można to także zapewnić pełne zabezpieczenia informacji kontekstowych jest przekazywany w operacji asynchronicznych lub punkty kodowe dostęp ograniczony kod.</span><span class="sxs-lookup"><span data-stu-id="9ee69-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="9ee69-112">`IHostSecurityContext` hermetyzuje informacje kontekstu zabezpieczeń, która jest nieprzezroczysta dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9ee69-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="9ee69-113">Środowisko uruchomieniowe rejestruje te informacje przy użyciu `Capture`, i przeniesieniu jej wątek puli procesów roboczych elementu wysyłania, finalizator wykonania i moduł i klasy konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="9ee69-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ee69-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ee69-114">Requirements</span></span>  
 <span data-ttu-id="9ee69-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ee69-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ee69-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ee69-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ee69-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ee69-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ee69-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ee69-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee69-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ee69-119">See also</span></span>

- [<span data-ttu-id="9ee69-120">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ee69-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="9ee69-121">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ee69-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="9ee69-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9ee69-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
