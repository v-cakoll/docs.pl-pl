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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118953"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="efafb-102">IHostAssemblyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="efafb-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="efafb-103">Udostępnia metody, które umożliwiają hosta określić zestawy zestawy, które powinny być załadowane przez środowisko uruchomieniowe języka wspólnego (CLR) lub przez hosta.</span><span class="sxs-lookup"><span data-stu-id="efafb-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efafb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="efafb-104">Methods</span></span>  
  
|<span data-ttu-id="efafb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="efafb-105">Method</span></span>|<span data-ttu-id="efafb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="efafb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="efafb-107">GetAssemblyStore, metoda</span><span class="sxs-lookup"><span data-stu-id="efafb-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="efafb-108">Pobiera wskaźnik interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) reprezentujący listę zestawy, ładowane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="efafb-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="efafb-109">GetNonHostStoreAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="efafb-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="efafb-110">Pobiera wskaźnik interfejsu do [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) reprezentujący listę zestawów, do których host oczekuje środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="efafb-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efafb-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efafb-111">Remarks</span></span>  
 <span data-ttu-id="efafb-112">Host nie jest wymagane do zaimplementowania `IHostAssemblyManager` lub `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="efafb-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="efafb-113">Jeśli host ma zaimplementowanego `IHostAssemblyManager`, musi implementować też `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="efafb-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="efafb-114">Środowisko uruchomieniowe wysyła zapytanie o `IHostAssemblyManager` przez wywołanie metody [ihostcontrol::gethostmanager —](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) po zainicjowaniu z `IID` z IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="efafb-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efafb-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efafb-115">Requirements</span></span>  
 <span data-ttu-id="efafb-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efafb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efafb-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="efafb-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efafb-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="efafb-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efafb-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efafb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efafb-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efafb-120">See also</span></span>

- [<span data-ttu-id="efafb-121">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="efafb-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="efafb-122">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="efafb-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="efafb-123">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="efafb-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="efafb-124">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="efafb-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
