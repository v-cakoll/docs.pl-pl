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
ms.openlocfilehash: 615637813b08629aaea74b23fa2737f52d61bafb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616921"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="96378-102">AssemblyBindInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="96378-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="96378-103">Zawiera szczegółowe informacje o przywoływanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="96378-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96378-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96378-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="96378-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="96378-105">Members</span></span>  
  
|<span data-ttu-id="96378-106">Członek</span><span class="sxs-lookup"><span data-stu-id="96378-106">Member</span></span>|<span data-ttu-id="96378-107">Opis</span><span class="sxs-lookup"><span data-stu-id="96378-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="96378-108">Unikatowy identyfikator `IStream` zwracanego przez wywołanie [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md), z którego ma zostać załadowany przywoływany zestaw.</span><span class="sxs-lookup"><span data-stu-id="96378-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="96378-109">Unikatowy identyfikator dla przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="96378-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="96378-110">Identyfikator zestawu, którego dotyczy odwołanie, po zastosowaniu wszystkich wartości zasad powiązań.</span><span class="sxs-lookup"><span data-stu-id="96378-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="96378-111">Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) wskazujących, które zasady przechowywania wersji (jeśli istnieją), należy zastosować do przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="96378-111">One of the [EPolicyAction](epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96378-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96378-112">Remarks</span></span>  
 <span data-ttu-id="96378-113">Host dostarcza unikatowy identyfikator `dwAppDomainId` do środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="96378-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="96378-114">Po wywołaniu `IHostAssemblyStore::ProvideAssembly` zwraca, środowisko uruchomieniowe używa identyfikatora, aby określić, czy zawartość `IStream` została zamapowana.</span><span class="sxs-lookup"><span data-stu-id="96378-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="96378-115">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię zamiast ponownego mapowania strumienia.</span><span class="sxs-lookup"><span data-stu-id="96378-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="96378-116">Środowisko uruchomieniowe używa również tego identyfikatora jako klucza wyszukiwania dla strumieni zwróconych z wywołań do [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="96378-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="96378-117">W związku z tym identyfikator musi być unikatowy dla żądań modułów i dla żądań zestawu.</span><span class="sxs-lookup"><span data-stu-id="96378-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96378-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96378-118">Requirements</span></span>  
 <span data-ttu-id="96378-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96378-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96378-120">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="96378-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="96378-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="96378-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96378-122">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96378-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96378-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96378-123">See also</span></span>

- [<span data-ttu-id="96378-124">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="96378-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="96378-125">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="96378-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="96378-126">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="96378-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="96378-127">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="96378-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="96378-128">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="96378-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="96378-129">ModuleBindInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="96378-129">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)
