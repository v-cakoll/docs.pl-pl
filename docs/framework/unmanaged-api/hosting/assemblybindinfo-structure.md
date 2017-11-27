---
title: "AssemblyBindInfo — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f23c8269c7dd7f85ad0f848c1dee2ed0bf903c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="c6278-102">AssemblyBindInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="c6278-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="c6278-103">Zawiera szczegółowe informacje dotyczące przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c6278-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6278-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6278-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="c6278-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c6278-105">Members</span></span>  
  
|<span data-ttu-id="c6278-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c6278-106">Member</span></span>|<span data-ttu-id="c6278-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c6278-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="c6278-108">Unikatowy identyfikator `IStream` zwrócony przez wywołanie do [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), z którym ma być załadowany przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c6278-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="c6278-109">Unikatowy identyfikator dla przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c6278-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="c6278-110">Identyfikator przywoływanego zestawu po zastosowaniu wartości zasad powiązania.</span><span class="sxs-lookup"><span data-stu-id="c6278-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="c6278-111">Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, które wskazują, które zasady przechowywania wersji, jeśli istnieje, ma zostać zastosowany do przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c6278-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6278-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6278-112">Remarks</span></span>  
 <span data-ttu-id="c6278-113">Host udostępnia unikatowy identyfikator `dwAppDomainId` się środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="c6278-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="c6278-114">Po wywołaniu `IHostAssemblyStore::ProvideAssembly` zwraca środowiska uruchomieniowego używa identyfikatora, aby określić, czy zawartość `IStream` zostały zamapowane.</span><span class="sxs-lookup"><span data-stu-id="c6278-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="c6278-115">Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię zamiast ponownego mapowania strumienia.</span><span class="sxs-lookup"><span data-stu-id="c6278-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="c6278-116">Środowisko uruchomieniowe również używa tego identyfikatora jako klucz wyszukiwania dla strumieni zwrócony z wywołań [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="c6278-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="c6278-117">W związku z tym identyfikator musi być unikatowy dla żądań modułu i żądań zestawów.</span><span class="sxs-lookup"><span data-stu-id="c6278-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6278-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6278-118">Requirements</span></span>  
 <span data-ttu-id="c6278-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6278-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6278-120">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="c6278-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c6278-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6278-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6278-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6278-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6278-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6278-123">See Also</span></span>  
 [<span data-ttu-id="c6278-124">Hosting — struktury</span><span class="sxs-lookup"><span data-stu-id="c6278-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="c6278-125">ICLRAssemblyIdentityManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="c6278-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="c6278-126">ICLRAssemblyReferenceList — interfejs</span><span class="sxs-lookup"><span data-stu-id="c6278-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="c6278-127">IHostAssemblyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="c6278-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="c6278-128">IHostAssemblyStore — interfejs</span><span class="sxs-lookup"><span data-stu-id="c6278-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="c6278-129">ModuleBindInfo — struktura</span><span class="sxs-lookup"><span data-stu-id="c6278-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
