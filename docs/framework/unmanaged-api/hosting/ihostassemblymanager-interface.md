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
ms.openlocfilehash: d9feeaf5f85d6f84a13e74a893b82c97fdaf023c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124507"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="5ae5a-102">IHostAssemblyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5ae5a-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="5ae5a-103">Dostarcza metody, które umożliwiają hostowi określenie zestawów zestawów, które powinny być ładowane przez środowisko uruchomieniowe języka wspólnego (CLR) lub hosta.</span><span class="sxs-lookup"><span data-stu-id="5ae5a-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ae5a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5ae5a-104">Methods</span></span>  
  
|<span data-ttu-id="5ae5a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5ae5a-105">Method</span></span>|<span data-ttu-id="5ae5a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5ae5a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ae5a-107">GetAssemblyStore, metoda</span><span class="sxs-lookup"><span data-stu-id="5ae5a-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="5ae5a-108">Pobiera wskaźnik interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , który reprezentuje listę zestawów załadowanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="5ae5a-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="5ae5a-109">GetNonHostStoreAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="5ae5a-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="5ae5a-110">Pobiera wskaźnik interfejsu do [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , który reprezentuje listę zestawów, które host oczekuje na załadowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5ae5a-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ae5a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ae5a-111">Remarks</span></span>  
 <span data-ttu-id="5ae5a-112">Host nie jest wymagany do implementowania `IHostAssemblyManager` ani `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="5ae5a-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="5ae5a-113">Jeśli Host implementuje `IHostAssemblyManager`, musi również implementować `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="5ae5a-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="5ae5a-114">Zapytania środowiska uruchomieniowego dla `IHostAssemblyManager` przez wywołanie [IHostControl:: GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) po inicjacji z `IID`em IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="5ae5a-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ae5a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ae5a-115">Requirements</span></span>  
 <span data-ttu-id="5ae5a-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ae5a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ae5a-117">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5ae5a-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ae5a-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ae5a-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ae5a-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ae5a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae5a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ae5a-120">See also</span></span>

- [<span data-ttu-id="5ae5a-121">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ae5a-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="5ae5a-122">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ae5a-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="5ae5a-123">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ae5a-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="5ae5a-124">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5ae5a-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
