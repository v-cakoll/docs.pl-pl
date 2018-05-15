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
ms.openlocfilehash: c8c8d17723481fc5b41fe5f3006fe8db2c53d1ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="7514e-102">IHostAssemblyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7514e-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="7514e-103">Udostępnia metody, które umożliwiają hosta określić zestawy zestawy, które powinny być załadowane przez środowisko uruchomieniowe języka wspólnego (CLR) lub przez hosta.</span><span class="sxs-lookup"><span data-stu-id="7514e-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7514e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7514e-104">Methods</span></span>  
  
|<span data-ttu-id="7514e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7514e-105">Method</span></span>|<span data-ttu-id="7514e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7514e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7514e-107">GetAssemblyStore, metoda</span><span class="sxs-lookup"><span data-stu-id="7514e-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="7514e-108">Pobiera wskaźnika interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) reprezentujący listę zestawów załadowanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="7514e-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="7514e-109">GetNonHostStoreAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="7514e-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="7514e-110">Pobiera wskaźnika interfejsu do [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) reprezentujący listę zestawów, które host oczekuje można załadować środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7514e-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7514e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7514e-111">Remarks</span></span>  
 <span data-ttu-id="7514e-112">Host nie jest wymagane do zaimplementowania `IHostAssemblyManager` lub `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="7514e-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="7514e-113">Jeśli host wdrożenia `IHostAssemblyManager`, musi implementować też `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="7514e-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="7514e-114">Środowisko uruchomieniowe kwerendy o `IHostAssemblyManager` przez wywołanie metody [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) po zainicjowaniu z `IID` z IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="7514e-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7514e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7514e-115">Requirements</span></span>  
 <span data-ttu-id="7514e-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7514e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7514e-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7514e-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7514e-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7514e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7514e-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7514e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7514e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7514e-120">See Also</span></span>  
 [<span data-ttu-id="7514e-121">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="7514e-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="7514e-122">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="7514e-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="7514e-123">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="7514e-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="7514e-124">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7514e-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
