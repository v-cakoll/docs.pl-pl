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
ms.openlocfilehash: d7475e2423d4dc6f57e8928514d7991169eef232
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124500"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="eb49f-102">IHostAssemblyStore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="eb49f-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="eb49f-103">Zapewnia metody, które pozwalają hostowi ładować zestawy i moduły niezależnie od środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="eb49f-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb49f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="eb49f-104">Methods</span></span>  
  
|<span data-ttu-id="eb49f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="eb49f-105">Method</span></span>|<span data-ttu-id="eb49f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="eb49f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb49f-107">ProvideAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="eb49f-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="eb49f-108">Pobiera odwołanie do zestawu, do którego nie odwołuje się [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwrócone z wywołania [IHostAssemblyManager:: GetNonHostStoreAssemblies —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="eb49f-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="eb49f-109">ProvideModule, metoda</span><span class="sxs-lookup"><span data-stu-id="eb49f-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="eb49f-110">Rozwiązuje moduł w zestawie lub połączonym (nieosadzonym) pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="eb49f-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb49f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb49f-111">Remarks</span></span>  
 <span data-ttu-id="eb49f-112">`IHostAssemblyStore` zapewnia sposób, aby Host ładował zestawy efektywnie w oparciu o tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="eb49f-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="eb49f-113">Host ładuje zestawy, zwracając `IStream` wystąpienia, które wskazują bezpośrednio w bajtach.</span><span class="sxs-lookup"><span data-stu-id="eb49f-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="eb49f-114">Środowisko CLR określa, czy host zaimplementował `IHostAssemblyStore` przez wywoływanie `IHostAssemblyManager::GetNonHostAssemblyStores` po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="eb49f-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="eb49f-115">Dzięki temu host może na przykład kontrolować powiązania z zestawami użytkowników, ale w celu utworzenia powiązania z zestawami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb49f-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb49f-116">W przypadku wdrażania `IHostAssemblyStore`Host określa jego zamiar w celu rozpoznania wszystkich zestawów, do których nie odwołuje się `ICLRAssemblyReferenceList` zwrócone przez `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="eb49f-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb49f-117">.NET Framework wersja 2,0 nie umożliwia hostowi załadowania obrazu natywnego zestawu, zgodnie z opisem w narzędziu [Native Image Generator (Ngen. exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="eb49f-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb49f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb49f-118">Requirements</span></span>  
 <span data-ttu-id="eb49f-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb49f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb49f-120">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eb49f-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb49f-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eb49f-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb49f-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb49f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb49f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb49f-123">See also</span></span>

- [<span data-ttu-id="eb49f-124">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb49f-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="eb49f-125">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb49f-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="eb49f-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="eb49f-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
