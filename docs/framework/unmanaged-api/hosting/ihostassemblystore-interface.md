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
ms.openlocfilehash: d4067c1fbcf99c903c892eaec58262d95569114b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61930042"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="18395-102">IHostAssemblyStore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="18395-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="18395-103">Udostępnia metody, które umożliwiają hosta można załadować zestawów i modułów, niezależnie od środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="18395-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18395-104">Metody</span><span class="sxs-lookup"><span data-stu-id="18395-104">Methods</span></span>  
  
|<span data-ttu-id="18395-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="18395-105">Method</span></span>|<span data-ttu-id="18395-106">Opis</span><span class="sxs-lookup"><span data-stu-id="18395-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18395-107">ProvideAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="18395-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="18395-108">Pobiera odwołanie do zestawu, który nie odwołuje się [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwrócony z wywołania do [ihostassemblymanager::getnonhoststoreassemblies —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="18395-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="18395-109">ProvideModule, metoda</span><span class="sxs-lookup"><span data-stu-id="18395-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="18395-110">Rozpoznaje modułu w obrębie zestawu lub plik połączony zasób (nie embedded).</span><span class="sxs-lookup"><span data-stu-id="18395-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18395-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="18395-111">Remarks</span></span>  
 <span data-ttu-id="18395-112">`IHostAssemblyStore` oferuje hosta można załadować zestawów, efektywnie oparte na tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="18395-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="18395-113">Host ładuje zestawy, zwracając `IStream` wystąpień, które wskazują bezpośrednio na bajty.</span><span class="sxs-lookup"><span data-stu-id="18395-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="18395-114">Środowisko CLR określa, czy host ma zaimplementowane `IHostAssemblyStore` przez wywołanie metody `IHostAssemblyManager::GetNonHostAssemblyStores` po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="18395-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="18395-115">Dzięki temu hosta, na przykład kontrolować powiązania do zestawów użytkownika, ale zależą od środowiska uruchomieniowego do powiązania do zestawów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18395-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18395-116">W dostarczaniu implementację `IHostAssemblyStore`, host Określa zamiar Rozwiąż wszystkie zestawy, które nie są przywoływane przez `ICLRAssemblyReferenceList` zwróciło `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="18395-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18395-117">.NET Framework w wersji 2.0 zapewnia możliwości dla hosta, który można załadować obrazu natywnego zestawu, zgodnie z informacjami od [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="18395-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18395-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18395-118">Requirements</span></span>  
 <span data-ttu-id="18395-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18395-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18395-120">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="18395-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18395-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18395-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18395-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18395-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18395-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18395-123">See also</span></span>

- [<span data-ttu-id="18395-124">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="18395-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="18395-125">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="18395-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="18395-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="18395-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
