---
title: ModuleBindInfo — Struktura
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f14d3dcaad1cc8cac11599b1647d61df3a793301
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124452"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="e664d-102">ModuleBindInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="e664d-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="e664d-103">Zawiera szczegółowe informacje o module odwołania i zestawu, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="e664d-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e664d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e664d-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="e664d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e664d-105">Members</span></span>  
  
|<span data-ttu-id="e664d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e664d-106">Member</span></span>|<span data-ttu-id="e664d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e664d-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="e664d-108">Unikatowy identyfikator `IStream` zwracanym przez wywołanie [ihostassemblystore::providemodule —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) metody, z którego ma zostać załadowany moduł odwołania.</span><span class="sxs-lookup"><span data-stu-id="e664d-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="e664d-109">Unikatowy identyfikator zestawu, który zawiera odwołania modułu.</span><span class="sxs-lookup"><span data-stu-id="e664d-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="e664d-110">Nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="e664d-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e664d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e664d-111">Remarks</span></span>  
 <span data-ttu-id="e664d-112">`ModuleBindInfo` jest przekazywany jako parametr do `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="e664d-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="e664d-113">Host dostarcza Unikatowy identyfikator `dwAppDomainId` na środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e664d-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="e664d-114">Po wywołaniu [ihostassemblystore::provideassembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) metoda zwróci wartość, środowisko wykonawcze używa identyfikatora do określenia, czy zawartość `IStream` zostały zamapowane.</span><span class="sxs-lookup"><span data-stu-id="e664d-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="e664d-115">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię, a nie ponowne mapowanie strumienia.</span><span class="sxs-lookup"><span data-stu-id="e664d-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="e664d-116">Środowisko wykonawcze używa również identyfikatorem jako klucz wyszukiwania dla strumieni, które są zwracane z wywołania `IHostAssemblyStore::ProvideAssembly` metody.</span><span class="sxs-lookup"><span data-stu-id="e664d-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="e664d-117">W związku z tym identyfikator musi być unikatowa dla żądań modułu, a także jak w przypadku żądań zestawu.</span><span class="sxs-lookup"><span data-stu-id="e664d-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e664d-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e664d-118">Requirements</span></span>  
 <span data-ttu-id="e664d-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e664d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e664d-120">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="e664d-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e664d-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e664d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e664d-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e664d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e664d-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e664d-123">See also</span></span>

- [<span data-ttu-id="e664d-124">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="e664d-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="e664d-125">AssemblyBindInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="e664d-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="e664d-126">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e664d-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="e664d-127">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="e664d-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e664d-128">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e664d-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
