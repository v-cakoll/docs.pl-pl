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
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133748"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="e3c6f-102">ModuleBindInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="e3c6f-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="e3c6f-103">Zawiera szczegółowe informacje dotyczące modułu, do którego istnieje odwołanie, i zestawu, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="e3c6f-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c6f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3c6f-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="e3c6f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e3c6f-105">Members</span></span>  
  
|<span data-ttu-id="e3c6f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e3c6f-106">Member</span></span>|<span data-ttu-id="e3c6f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e3c6f-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="e3c6f-108">Unikatowy identyfikator `IStream`, który jest zwracany przez wywołanie metody [IHostAssemblyStore::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) , z której ma zostać załadowany moduł, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="e3c6f-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="e3c6f-109">Unikatowy identyfikator zestawu, który zawiera moduł, do którego się odwoływano.</span><span class="sxs-lookup"><span data-stu-id="e3c6f-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="e3c6f-110">Nazwa modułu, do którego się odwoływano.</span><span class="sxs-lookup"><span data-stu-id="e3c6f-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3c6f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3c6f-111">Remarks</span></span>  
 <span data-ttu-id="e3c6f-112">`ModuleBindInfo` jest przenoszona jako parametr do `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="e3c6f-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="e3c6f-113">Host dostarcza unikatowy identyfikator `dwAppDomainId` do środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e3c6f-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="e3c6f-114">Po wywołaniu metody [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) , środowisko uruchomieniowe użyje identyfikatora, aby określić, czy zawartość `IStream` została zamapowana.</span><span class="sxs-lookup"><span data-stu-id="e3c6f-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="e3c6f-115">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię zamiast ponownego mapowania strumienia.</span><span class="sxs-lookup"><span data-stu-id="e3c6f-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="e3c6f-116">Środowisko uruchomieniowe używa również tego identyfikatora jako klucza wyszukiwania dla strumieni, które są zwracane z wywołań metody `IHostAssemblyStore::ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e3c6f-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="e3c6f-117">W związku z tym identyfikator musi być unikatowy w przypadku żądań modułu, a także dla żądań zestawu.</span><span class="sxs-lookup"><span data-stu-id="e3c6f-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c6f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3c6f-118">Requirements</span></span>  
 <span data-ttu-id="e3c6f-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c6f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c6f-120">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="e3c6f-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e3c6f-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3c6f-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3c6f-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c6f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c6f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3c6f-123">See also</span></span>

- [<span data-ttu-id="e3c6f-124">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="e3c6f-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="e3c6f-125">AssemblyBindInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="e3c6f-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="e3c6f-126">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c6f-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="e3c6f-127">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c6f-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e3c6f-128">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c6f-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
