---
title: IHostAssemblyStore — Interfejs
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f881440b2e93745723bd090cfbab0286dcd0a4e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937876"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="bfaaf-102">IHostAssemblyStore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bfaaf-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="bfaaf-103">Zapewnia metody, które pozwalają hostowi ładować zestawy i moduły niezależnie od środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="bfaaf-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bfaaf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bfaaf-104">Methods</span></span>  
  
|<span data-ttu-id="bfaaf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bfaaf-105">Method</span></span>|<span data-ttu-id="bfaaf-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bfaaf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bfaaf-107">ProvideAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="bfaaf-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="bfaaf-108">Pobiera odwołanie do zestawu, do którego nie odwołuje się [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwrócone z wywołania [IHostAssemblyManager:: GetNonHostStoreAssemblies —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="bfaaf-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="bfaaf-109">ProvideModule, metoda</span><span class="sxs-lookup"><span data-stu-id="bfaaf-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="bfaaf-110">Rozwiązuje moduł w zestawie lub połączonym (nieosadzonym) pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfaaf-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfaaf-111">Remarks</span></span>  
 <span data-ttu-id="bfaaf-112">`IHostAssemblyStore`umożliwia hostowi wydajne ładowanie zestawów w oparciu o tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="bfaaf-113">Host ładuje zestawy, zwracając `IStream` wystąpienia bezpośrednio w bajtach.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="bfaaf-114">Środowisko CLR określa, czy host został zaimplementowany `IHostAssemblyStore` przez wywołanie `IHostAssemblyManager::GetNonHostAssemblyStores` przy inicjacji.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="bfaaf-115">Dzięki temu host może na przykład kontrolować powiązania z zestawami użytkowników, ale w celu utworzenia powiązania z zestawami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfaaf-116">W przypadku wdrażania programu `IHostAssemblyStore`Host określa jego zamiar, aby rozpoznać wszystkie zestawy, do których nie odwołują `ICLRAssemblyReferenceList` się zwrócone z `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="bfaaf-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfaaf-117">.NET Framework wersja 2,0 nie umożliwia hostowi załadowania obrazu natywnego zestawu, zgodnie z opisem w narzędziu [Native Image Generator (Ngen. exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="bfaaf-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfaaf-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfaaf-118">Requirements</span></span>  
 <span data-ttu-id="bfaaf-119">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfaaf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfaaf-120">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bfaaf-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfaaf-121">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bfaaf-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfaaf-122">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfaaf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfaaf-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfaaf-123">See also</span></span>

- [<span data-ttu-id="bfaaf-124">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfaaf-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="bfaaf-125">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfaaf-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="bfaaf-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bfaaf-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
