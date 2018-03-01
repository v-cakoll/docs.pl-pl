---
title: "ICLRAssemblyIdentityManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 168c67eb701d7dfc461553cfe32ed43dcea5e844
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="db508-102">ICLRAssemblyIdentityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="db508-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="db508-103">Udostępnia metody, które obsługują komunikację między hostem i środowisko uruchomieniowe języka wspólnego (CLR) informacje o zestawach.</span><span class="sxs-lookup"><span data-stu-id="db508-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db508-104">Metody</span><span class="sxs-lookup"><span data-stu-id="db508-104">Methods</span></span>  
  
|<span data-ttu-id="db508-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="db508-105">Method</span></span>|<span data-ttu-id="db508-106">Opis</span><span class="sxs-lookup"><span data-stu-id="db508-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db508-107">GetBindingIdentityFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="db508-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="db508-108">Pobiera tożsamość zestawu powiązania danych dla zestawu przy użyciu określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="db508-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="db508-109">GetBindingIdentityFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="db508-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="db508-110">Pobiera canonical zestawu danych tożsamości dla zestawu w określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="db508-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="db508-111">GetCLRAssemblyReferenceList, metoda</span><span class="sxs-lookup"><span data-stu-id="db508-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="db508-112">Pobiera [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) wystąpienia z podanej listy tożsamości zestawu częściowej.</span><span class="sxs-lookup"><span data-stu-id="db508-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="db508-113">GetProbingAssembliesFromReference, metoda</span><span class="sxs-lookup"><span data-stu-id="db508-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="db508-114">Pobiera [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) modułu wyliczającego dla tożsamości zestawu odwołuje się zestaw o określonej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="db508-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="db508-115">GetReferencedAssembliesFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="db508-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="db508-116">Pobiera [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) wystąpienia, które zawiera listę zestawów odwołuje się zestaw przy użyciu określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="db508-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="db508-117">GetReferencedAssembliesFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="db508-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="db508-118">Pobiera wskaźnik do `ICLRReferenceAssemblyEnum` obiekt zawierający dane tożsamości zestawu dla zestawów odwołuje się zestaw w określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="db508-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="db508-119">IsStronglyNamed, metoda</span><span class="sxs-lookup"><span data-stu-id="db508-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="db508-120">Pobiera wartość wskazującą, czy określony zestaw ma silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="db508-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db508-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db508-121">Remarks</span></span>  
 <span data-ttu-id="db508-122">Użyj `ICLRAssemblyIdentityManager` można pobrać wystąpień `ICLRAssemblyReferenceList` i wyliczyć tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="db508-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db508-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db508-123">Requirements</span></span>  
 <span data-ttu-id="db508-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db508-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db508-125">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db508-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db508-126">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db508-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db508-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db508-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db508-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db508-128">See Also</span></span>  
 [<span data-ttu-id="db508-129">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="db508-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="db508-130">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="db508-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="db508-131">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="db508-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
