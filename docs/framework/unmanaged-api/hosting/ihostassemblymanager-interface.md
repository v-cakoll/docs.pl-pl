---
title: IHostAssemblyManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e300d4645939a131ceb8206999d95056b96a678
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118953"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="014bc-102">IHostAssemblyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="014bc-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="014bc-103">Udostępnia metody, które umożliwiają hosta określić zestawy zestawy, które powinny być załadowane przez środowisko uruchomieniowe języka wspólnego (CLR) lub przez hosta.</span><span class="sxs-lookup"><span data-stu-id="014bc-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="014bc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="014bc-104">Methods</span></span>  
  
|<span data-ttu-id="014bc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="014bc-105">Method</span></span>|<span data-ttu-id="014bc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="014bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="014bc-107">GetAssemblyStore, metoda</span><span class="sxs-lookup"><span data-stu-id="014bc-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="014bc-108">Pobiera wskaźnik interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) reprezentujący listę zestawy, ładowane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="014bc-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="014bc-109">GetNonHostStoreAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="014bc-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="014bc-110">Pobiera wskaźnik interfejsu do [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) reprezentujący listę zestawów, do których host oczekuje środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="014bc-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="014bc-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="014bc-111">Remarks</span></span>  
 <span data-ttu-id="014bc-112">Host nie jest wymagane do zaimplementowania `IHostAssemblyManager` lub `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="014bc-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="014bc-113">Jeśli host ma zaimplementowanego `IHostAssemblyManager`, musi implementować też `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="014bc-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="014bc-114">Środowisko uruchomieniowe wysyła zapytanie o `IHostAssemblyManager` przez wywołanie metody [ihostcontrol::gethostmanager —](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) po zainicjowaniu z `IID` z IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="014bc-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="014bc-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="014bc-115">Requirements</span></span>  
 <span data-ttu-id="014bc-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="014bc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="014bc-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="014bc-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="014bc-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="014bc-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="014bc-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="014bc-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="014bc-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="014bc-120">See also</span></span>

- [<span data-ttu-id="014bc-121">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="014bc-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="014bc-122">IHostAssemblyStore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="014bc-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="014bc-123">IHostControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="014bc-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="014bc-124">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="014bc-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
