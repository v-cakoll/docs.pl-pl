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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f4cb71e5ac0afe19e865ffca6fe578ad08f3162
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773867"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="10e6c-102">AssemblyBindInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="10e6c-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="10e6c-103">Zawiera szczegółowe informacje o zestawie, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="10e6c-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10e6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10e6c-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="10e6c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="10e6c-105">Members</span></span>  
  
|<span data-ttu-id="10e6c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="10e6c-106">Member</span></span>|<span data-ttu-id="10e6c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="10e6c-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="10e6c-108">Unikatowy identyfikator `IStream` zwracany przez wywołanie [ihostassemblystore::provideassembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), z którym przywoływany zestaw ma być załadowany.</span><span class="sxs-lookup"><span data-stu-id="10e6c-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="10e6c-109">Unikatowy identyfikator dla przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="10e6c-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="10e6c-110">Identyfikator przywoływanego zestawu po zastosowaniu dowolnej wartości zasad wiązania.</span><span class="sxs-lookup"><span data-stu-id="10e6c-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="10e6c-111">Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, które wskazują, które zasady przechowywania wersji, powinny być stosowane do przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="10e6c-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10e6c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10e6c-112">Remarks</span></span>  
 <span data-ttu-id="10e6c-113">Host dostarcza Unikatowy identyfikator `dwAppDomainId` na środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="10e6c-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="10e6c-114">Po wywołaniu `IHostAssemblyStore::ProvideAssembly` zwróci wartość, środowisko wykonawcze używa identyfikatora do określenia, czy zawartość `IStream` zostały zamapowane.</span><span class="sxs-lookup"><span data-stu-id="10e6c-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="10e6c-115">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię, a nie ponowne mapowanie strumienia.</span><span class="sxs-lookup"><span data-stu-id="10e6c-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="10e6c-116">Środowisko wykonawcze używa również identyfikatorem jako klucz wyszukiwania dla strumieni zwrócony z wywołania [ihostassemblystore::providemodule —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="10e6c-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="10e6c-117">W związku z tym identyfikator musi być unikatowa, żądań modułu i żądań zestawu.</span><span class="sxs-lookup"><span data-stu-id="10e6c-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10e6c-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10e6c-118">Requirements</span></span>  
 <span data-ttu-id="10e6c-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10e6c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10e6c-120">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="10e6c-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="10e6c-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10e6c-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10e6c-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10e6c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e6c-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10e6c-123">See also</span></span>

- [<span data-ttu-id="10e6c-124">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="10e6c-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="10e6c-125">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="10e6c-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="10e6c-126">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="10e6c-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="10e6c-127">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="10e6c-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="10e6c-128">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="10e6c-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="10e6c-129">ModuleBindInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="10e6c-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
