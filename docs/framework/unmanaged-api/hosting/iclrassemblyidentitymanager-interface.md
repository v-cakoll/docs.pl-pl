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
ms.openlocfilehash: 26de2ebf1364981d8b8f1fb38c8fa1045191114f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126624"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="bfcae-102">ICLRAssemblyIdentityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bfcae-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="bfcae-103">Zapewnia metody obsługujące komunikację między hostem i środowiskiem uruchomieniowym języka wspólnego (CLR) dotyczące zestawów.</span><span class="sxs-lookup"><span data-stu-id="bfcae-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bfcae-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bfcae-104">Methods</span></span>  
  
|<span data-ttu-id="bfcae-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bfcae-105">Method</span></span>|<span data-ttu-id="bfcae-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bfcae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bfcae-107">GetBindingIdentityFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="bfcae-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="bfcae-108">Pobiera dane powiązania tożsamości zestawu z określoną ścieżką do pliku.</span><span class="sxs-lookup"><span data-stu-id="bfcae-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="bfcae-109">GetBindingIdentityFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="bfcae-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="bfcae-110">Pobiera dane tożsamości zestawu kanonicznego dla zestawu w określonym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="bfcae-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="bfcae-111">GetCLRAssemblyReferenceList, metoda</span><span class="sxs-lookup"><span data-stu-id="bfcae-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="bfcae-112">Pobiera wystąpienie [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) z podanej listy tożsamości zestawów częściowych.</span><span class="sxs-lookup"><span data-stu-id="bfcae-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="bfcae-113">GetProbingAssembliesFromReference, metoda</span><span class="sxs-lookup"><span data-stu-id="bfcae-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="bfcae-114">Pobiera moduł wyliczający [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) dla tożsamości zestawu, do których odwołuje się zestaw z określoną tożsamością.</span><span class="sxs-lookup"><span data-stu-id="bfcae-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="bfcae-115">GetReferencedAssembliesFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="bfcae-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="bfcae-116">Pobiera wystąpienie [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) , które zawiera listę zestawów, do których odwołuje się zestaw w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="bfcae-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="bfcae-117">GetReferencedAssembliesFromStream, metoda</span><span class="sxs-lookup"><span data-stu-id="bfcae-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="bfcae-118">Pobiera wskaźnik do obiektu `ICLRReferenceAssemblyEnum`, który zawiera dane tożsamości zestawu dla zestawów, do których odwołuje się zestaw w określonym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="bfcae-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="bfcae-119">IsStronglyNamed, metoda</span><span class="sxs-lookup"><span data-stu-id="bfcae-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="bfcae-120">Pobiera wartość wskazującą, czy określony zestaw ma silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="bfcae-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfcae-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfcae-121">Remarks</span></span>  
 <span data-ttu-id="bfcae-122">Użyj `ICLRAssemblyIdentityManager`, aby uzyskać wystąpienia `ICLRAssemblyReferenceList` i wyliczania tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="bfcae-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfcae-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfcae-123">Requirements</span></span>  
 <span data-ttu-id="bfcae-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfcae-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfcae-125">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bfcae-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfcae-126">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bfcae-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfcae-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfcae-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfcae-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfcae-128">See also</span></span>

- [<span data-ttu-id="bfcae-129">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfcae-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="bfcae-130">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfcae-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="bfcae-131">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bfcae-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
