---
title: "IHostAssemblyStore — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c795d4baa3030817299f23c3dadf4caf7a5edc5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="c445a-102">IHostAssemblyStore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c445a-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="c445a-103">Udostępnia metody umożliwiające hosta można załadować zestawów i modułów, niezależnie od środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="c445a-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c445a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c445a-104">Methods</span></span>  
  
|<span data-ttu-id="c445a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c445a-105">Method</span></span>|<span data-ttu-id="c445a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c445a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c445a-107">ProvideAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="c445a-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="c445a-108">Pobiera odwołanie do zestawu, który nie jest wywoływany przez [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwrócone w wyniku wywołania [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="c445a-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="c445a-109">ProvideModule, metoda</span><span class="sxs-lookup"><span data-stu-id="c445a-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="c445a-110">Rozpoznaje modułu w ramach zestawu lub połączonego pliku zasobów (nie embedded).</span><span class="sxs-lookup"><span data-stu-id="c445a-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c445a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c445a-111">Remarks</span></span>  
 <span data-ttu-id="c445a-112">`IHostAssemblyStore`Umożliwia ładowanie zestawów wydajnie oparte na tożsamości zestawu hosta.</span><span class="sxs-lookup"><span data-stu-id="c445a-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="c445a-113">Host ładuje zestawy zwracając `IStream` wystąpień, które wskazują bezpośrednio na bajty.</span><span class="sxs-lookup"><span data-stu-id="c445a-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="c445a-114">Środowisko CLR określa, czy host ma zaimplementowany `IHostAssemblyStore` przez wywołanie metody `IHostAssemblyManager::GetNonHostAssemblyStores` po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="c445a-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="c445a-115">Dzięki temu hosta, na przykład kontrolować powiązania zestawów użytkownika, ale zależą od środowiska wykonawczego, aby powiązać zestawy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c445a-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c445a-116">Dostarczając implementację `IHostAssemblyStore`, host Określa chęć rozwiązać wszystkie zestawy, których nie odwołuje się `ICLRAssemblyReferenceList` zwrócony z `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="c445a-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c445a-117">.NET Framework w wersji 2.0 nie umożliwiają na załadowanie obrazu macierzystego zestawu hosta dostarczone przez [Generator obrazu natywnego (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c445a-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c445a-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c445a-118">Requirements</span></span>  
 <span data-ttu-id="c445a-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c445a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c445a-120">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c445a-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c445a-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c445a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c445a-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c445a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c445a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c445a-123">See Also</span></span>  
 [<span data-ttu-id="c445a-124">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="c445a-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="c445a-125">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c445a-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="c445a-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c445a-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
