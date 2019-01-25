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
ms.openlocfilehash: 0e60b578256fb516ee0bd4edcec0b5a1a5179b46
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615338"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="fb1ee-102">IHostAssemblyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fb1ee-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="fb1ee-103">Udostępnia metody, które umożliwiają hosta określić zestawy zestawy, które powinny być załadowane przez środowisko uruchomieniowe języka wspólnego (CLR) lub przez hosta.</span><span class="sxs-lookup"><span data-stu-id="fb1ee-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb1ee-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fb1ee-104">Methods</span></span>  
  
|<span data-ttu-id="fb1ee-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fb1ee-105">Method</span></span>|<span data-ttu-id="fb1ee-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fb1ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb1ee-107">GetAssemblyStore, metoda</span><span class="sxs-lookup"><span data-stu-id="fb1ee-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="fb1ee-108">Pobiera wskaźnik interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) reprezentujący listę zestawy, ładowane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="fb1ee-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="fb1ee-109">GetNonHostStoreAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="fb1ee-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="fb1ee-110">Pobiera wskaźnik interfejsu do [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) reprezentujący listę zestawów, do których host oczekuje środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="fb1ee-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb1ee-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb1ee-111">Remarks</span></span>  
 <span data-ttu-id="fb1ee-112">Host nie jest wymagane do zaimplementowania `IHostAssemblyManager` lub `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="fb1ee-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="fb1ee-113">Jeśli host ma zaimplementowanego `IHostAssemblyManager`, musi implementować też `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="fb1ee-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="fb1ee-114">Środowisko uruchomieniowe wysyła zapytanie o `IHostAssemblyManager` przez wywołanie metody [ihostcontrol::gethostmanager —](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) po zainicjowaniu z `IID` z IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="fb1ee-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb1ee-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb1ee-115">Requirements</span></span>  
 <span data-ttu-id="fb1ee-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb1ee-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb1ee-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb1ee-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb1ee-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb1ee-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb1ee-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb1ee-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1ee-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb1ee-120">See also</span></span>
- [<span data-ttu-id="fb1ee-121">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb1ee-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="fb1ee-122">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb1ee-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="fb1ee-123">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb1ee-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="fb1ee-124">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fb1ee-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
