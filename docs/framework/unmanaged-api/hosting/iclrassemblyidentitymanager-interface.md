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
ms.openlocfilehash: f06c8228d5eb850c0d5ff94d12be03d7fb75023b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615920"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="d103d-102">ICLRAssemblyIdentityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d103d-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="d103d-103">Zapewnia metody obsługujące komunikację między hostem i środowiskiem uruchomieniowym języka wspólnego (CLR) dotyczące zestawów.</span><span class="sxs-lookup"><span data-stu-id="d103d-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d103d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d103d-104">Methods</span></span>  
  
|<span data-ttu-id="d103d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d103d-105">Method</span></span>|<span data-ttu-id="d103d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d103d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d103d-107">GetBindingIdentityFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="d103d-107">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="d103d-108">Pobiera dane powiązania tożsamości zestawu z określoną ścieżką do pliku.</span><span class="sxs-lookup"><span data-stu-id="d103d-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="d103d-109">GetBindingIdentityFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="d103d-109">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="d103d-110">Pobiera dane tożsamości zestawu kanonicznego dla zestawu w określonym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="d103d-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="d103d-111">GetCLRAssemblyReferenceList, metoda</span><span class="sxs-lookup"><span data-stu-id="d103d-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="d103d-112">Pobiera wystąpienie [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) z podanej listy tożsamości zestawów częściowych.</span><span class="sxs-lookup"><span data-stu-id="d103d-112">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="d103d-113">GetProbingAssembliesFromReference, metoda</span><span class="sxs-lookup"><span data-stu-id="d103d-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="d103d-114">Pobiera moduł wyliczający [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) dla tożsamości zestawu, do których odwołuje się zestaw z określoną tożsamością.</span><span class="sxs-lookup"><span data-stu-id="d103d-114">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="d103d-115">GetReferencedAssembliesFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="d103d-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="d103d-116">Pobiera wystąpienie [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) , które zawiera listę zestawów, do których odwołuje się zestaw w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="d103d-116">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="d103d-117">GetReferencedAssembliesFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="d103d-117">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="d103d-118">Pobiera wskaźnik do `ICLRReferenceAssemblyEnum` obiektu, który zawiera dane tożsamości zestawu dla zestawów, do których odwołuje się zestaw w określonym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="d103d-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="d103d-119">IsStronglyNamed, metoda</span><span class="sxs-lookup"><span data-stu-id="d103d-119">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="d103d-120">Pobiera wartość wskazującą, czy określony zestaw ma silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="d103d-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d103d-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d103d-121">Remarks</span></span>  
 <span data-ttu-id="d103d-122">Służy `ICLRAssemblyIdentityManager` do pobierania wystąpień `ICLRAssemblyReferenceList` i wyliczania tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="d103d-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d103d-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d103d-123">Requirements</span></span>  
 <span data-ttu-id="d103d-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d103d-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d103d-125">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d103d-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d103d-126">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d103d-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d103d-127">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d103d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d103d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d103d-128">See also</span></span>

- [<span data-ttu-id="d103d-129">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d103d-129">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d103d-130">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="d103d-130">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="d103d-131">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d103d-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
