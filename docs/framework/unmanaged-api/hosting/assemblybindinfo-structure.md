---
title: AssemblyBindInfo — Struktura
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 8764a3d665c997460419561eb168f92ca769c30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192112"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="cfccc-102">AssemblyBindInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="cfccc-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="cfccc-103">Zawiera szczegółowe informacje o przywoływanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="cfccc-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfccc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfccc-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="cfccc-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="cfccc-105">Members</span></span>  
  
|<span data-ttu-id="cfccc-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="cfccc-106">Member</span></span>|<span data-ttu-id="cfccc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cfccc-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="cfccc-108">Unikatowy identyfikator `IStream` zwrócone przez wywołanie [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), z którego ma zostać załadowany przywoływany zestaw.</span><span class="sxs-lookup"><span data-stu-id="cfccc-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="cfccc-109">Unikatowy identyfikator dla przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cfccc-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="cfccc-110">Identyfikator zestawu, którego dotyczy odwołanie, po zastosowaniu wszystkich wartości zasad powiązań.</span><span class="sxs-lookup"><span data-stu-id="cfccc-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="cfccc-111">Jedna z wartości [EPolicyAction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wskazujących, które zasady przechowywania wersji (jeśli istnieją), należy zastosować do przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cfccc-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfccc-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfccc-112">Remarks</span></span>  
 <span data-ttu-id="cfccc-113">Host dostarcza unikatowy identyfikator `dwAppDomainId` do środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="cfccc-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="cfccc-114">Po wywołaniu `IHostAssemblyStore::ProvideAssembly` zwraca, środowisko uruchomieniowe używa identyfikatora, aby określić, czy zawartość `IStream` została zmapowana.</span><span class="sxs-lookup"><span data-stu-id="cfccc-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="cfccc-115">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię zamiast ponownego mapowania strumienia.</span><span class="sxs-lookup"><span data-stu-id="cfccc-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="cfccc-116">Środowisko uruchomieniowe używa również tego identyfikatora jako klucza wyszukiwania dla strumieni zwróconych z wywołań do [IHostAssemblyStore::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="cfccc-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="cfccc-117">W związku z tym identyfikator musi być unikatowy dla żądań modułów i dla żądań zestawu.</span><span class="sxs-lookup"><span data-stu-id="cfccc-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfccc-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfccc-118">Requirements</span></span>  
 <span data-ttu-id="cfccc-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfccc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfccc-120">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="cfccc-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="cfccc-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cfccc-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfccc-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfccc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfccc-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfccc-123">See also</span></span>

- [<span data-ttu-id="cfccc-124">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="cfccc-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="cfccc-125">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfccc-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="cfccc-126">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfccc-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="cfccc-127">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfccc-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="cfccc-128">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfccc-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="cfccc-129">ModuleBindInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="cfccc-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
