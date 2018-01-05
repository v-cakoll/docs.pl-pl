---
title: "ModuleBindInfo — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ModuleBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ModuleBindInfo
helpviewer_keywords: ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399ba2471b4dc7c5e372a56a9dcab8117068a693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="161a1-102">ModuleBindInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="161a1-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="161a1-103">Zawiera szczegółowe informacje o module przywoływany i zestawu, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="161a1-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="161a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="161a1-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="161a1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="161a1-105">Members</span></span>  
  
|<span data-ttu-id="161a1-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="161a1-106">Member</span></span>|<span data-ttu-id="161a1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="161a1-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="161a1-108">Unikatowy identyfikator `IStream` który jest zwracany przez wywołanie do [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) metody, z którego ma zostać załadowany moduł, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="161a1-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="161a1-109">Unikatowy identyfikator dla zestawu, który zawiera modułu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="161a1-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="161a1-110">Nazwa modułu do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="161a1-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="161a1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="161a1-111">Remarks</span></span>  
 <span data-ttu-id="161a1-112">`ModuleBindInfo`jest przekazywana jako parametr `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="161a1-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="161a1-113">Host udostępnia unikatowy identyfikator `dwAppDomainId` się środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="161a1-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="161a1-114">Po wywołaniu [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) metoda zwróci wartość, środowisko uruchomieniowe używa identyfikatora w celu określenia, czy zawartość `IStream` zostały zamapowane.</span><span class="sxs-lookup"><span data-stu-id="161a1-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="161a1-115">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię zamiast ponownego mapowania strumienia.</span><span class="sxs-lookup"><span data-stu-id="161a1-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="161a1-116">Środowisko uruchomieniowe również używa tego identyfikatora jako klucz wyszukiwania dla strumieni, które są zwracane z wywołań `IHostAssemblyStore::ProvideAssembly` metody.</span><span class="sxs-lookup"><span data-stu-id="161a1-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="161a1-117">W związku z tym identyfikatorem musi być unikatowa dla żądań modułu również podobnie jak w przypadku żądań zestawów.</span><span class="sxs-lookup"><span data-stu-id="161a1-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="161a1-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="161a1-118">Requirements</span></span>  
 <span data-ttu-id="161a1-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="161a1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="161a1-120">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="161a1-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="161a1-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="161a1-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="161a1-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="161a1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161a1-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="161a1-123">See Also</span></span>  
 [<span data-ttu-id="161a1-124">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="161a1-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="161a1-125">AssemblyBindInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="161a1-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [<span data-ttu-id="161a1-126">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="161a1-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="161a1-127">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="161a1-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="161a1-128">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="161a1-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
