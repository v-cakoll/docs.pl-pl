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
ms.openlocfilehash: 993d16818b25dfefe1f53c7afd06bc9857d9eb24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121521"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="daa23-102">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="daa23-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="daa23-103">Umożliwia środowisko uruchomieniowe języka wspólnego (CLR), aby zachować informacje kontekstu zabezpieczeń zaimplementowane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="daa23-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="daa23-104">Metody</span><span class="sxs-lookup"><span data-stu-id="daa23-104">Methods</span></span>  
  
|<span data-ttu-id="daa23-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="daa23-105">Method</span></span>|<span data-ttu-id="daa23-106">Opis</span><span class="sxs-lookup"><span data-stu-id="daa23-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="daa23-107">Capture, metoda</span><span class="sxs-lookup"><span data-stu-id="daa23-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="daa23-108">Pobiera klon wystąpienia `IHostSecurityContext` zwróconego przez wywołanie [IHostSecurityManager:: GetSecurityContext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="daa23-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daa23-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="daa23-109">Remarks</span></span>  
 <span data-ttu-id="daa23-110">Host może kontrolować cały dostęp kodu do tokenów wątków przez środowisko CLR i kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="daa23-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="daa23-111">Może także zapewnić, że pełne informacje kontekstu zabezpieczeń są przesyłane przez operacje asynchroniczne lub punkty kodowe z ograniczonym dostępem do kodu.</span><span class="sxs-lookup"><span data-stu-id="daa23-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="daa23-112">`IHostSecurityContext` hermetyzuje informacje kontekstu zabezpieczeń, nieprzezroczyste dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="daa23-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="daa23-113">Środowisko uruchomieniowe przechwytuje te informacje przy użyciu `Capture`i przenosi je między elementami roboczymi puli wątków, wykonywaniem finalizatorów oraz konstruktorami modułów i klas.</span><span class="sxs-lookup"><span data-stu-id="daa23-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daa23-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="daa23-114">Requirements</span></span>  
 <span data-ttu-id="daa23-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daa23-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daa23-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="daa23-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="daa23-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="daa23-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="daa23-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daa23-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa23-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="daa23-119">See also</span></span>

- [<span data-ttu-id="daa23-120">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="daa23-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="daa23-121">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="daa23-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="daa23-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="daa23-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
