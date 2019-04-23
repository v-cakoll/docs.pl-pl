---
title: ICLRAssemblyIdentityManager — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b209e568b1e65ed785155d045cd48d1248672da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209804"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="e4e1a-102">ICLRAssemblyIdentityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e4e1a-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="e4e1a-103">Udostępnia metody, które obsługują komunikację między hostem i środowisko uruchomieniowe języka wspólnego (CLR) informacje o zestawach.</span><span class="sxs-lookup"><span data-stu-id="e4e1a-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4e1a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e4e1a-104">Methods</span></span>  
  
|<span data-ttu-id="e4e1a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e4e1a-105">Method</span></span>|<span data-ttu-id="e4e1a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e4e1a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4e1a-107">GetBindingIdentityFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="e4e1a-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="e4e1a-108">Pobiera tożsamość zestawu, wiązanie danych do zestawu w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="e4e1a-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="e4e1a-109">GetBindingIdentityFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="e4e1a-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="e4e1a-110">Pobiera dane tożsamości canonical zestawu dla zestawu w określonej usłudze stream.</span><span class="sxs-lookup"><span data-stu-id="e4e1a-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="e4e1a-111">GetCLRAssemblyReferenceList, metoda</span><span class="sxs-lookup"><span data-stu-id="e4e1a-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="e4e1a-112">Pobiera [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) wystąpienia z podanej listy tożsamości zestawu częściowego.</span><span class="sxs-lookup"><span data-stu-id="e4e1a-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="e4e1a-113">GetProbingAssembliesFromReference, metoda</span><span class="sxs-lookup"><span data-stu-id="e4e1a-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="e4e1a-114">Pobiera [iclrprobingassemblyenum —](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) modułu wyliczającego dla tożsamości zestawu odwołuje się zestaw o określonej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="e4e1a-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="e4e1a-115">GetReferencedAssembliesFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="e4e1a-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="e4e1a-116">Pobiera [iclrreferenceassemblyenum —](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) wystąpienia, które zawiera listę zestawów, które odwołuje się zestaw w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="e4e1a-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="e4e1a-117">GetReferencedAssembliesFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="e4e1a-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="e4e1a-118">Pobiera wskaźnik do `ICLRReferenceAssemblyEnum` obiekt, który zawiera dane o tożsamości zestawu dla zestawów odwołuje się zestaw w określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="e4e1a-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="e4e1a-119">IsStronglyNamed, metoda</span><span class="sxs-lookup"><span data-stu-id="e4e1a-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="e4e1a-120">Pobiera wartość wskazującą, czy określony zestaw ma silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e4e1a-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4e1a-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4e1a-121">Remarks</span></span>  
 <span data-ttu-id="e4e1a-122">Użyj `ICLRAssemblyIdentityManager` można pobrać wystąpień `ICLRAssemblyReferenceList` i wyliczania tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="e4e1a-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4e1a-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4e1a-123">Requirements</span></span>  
 <span data-ttu-id="e4e1a-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4e1a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4e1a-125">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4e1a-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4e1a-126">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4e1a-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4e1a-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4e1a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e1a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4e1a-128">See also</span></span>

- [<span data-ttu-id="e4e1a-129">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4e1a-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e4e1a-130">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4e1a-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="e4e1a-131">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e4e1a-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
