---
title: EBindPolicyLevels — Wyliczenie
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8f2b08662e719a3308a62ab5b60f5dc490f2a6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142210"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="b8f37-102">EBindPolicyLevels — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b8f37-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="b8f37-103">Zawiera flagi, aby określić poziom, na którym można zastosować lub zmodyfikować zasady zestawu.</span><span class="sxs-lookup"><span data-stu-id="b8f37-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8f37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8f37-104">Syntax</span></span>  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="b8f37-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b8f37-105">Members</span></span>  
  
|<span data-ttu-id="b8f37-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b8f37-106">Member</span></span>|<span data-ttu-id="b8f37-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b8f37-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="b8f37-108">Określa, czy zasady mają być stosowane na poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="b8f37-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="b8f37-109">Określa, czy zasady mają być stosowane na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b8f37-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="b8f37-110">Określa, czy zasady mają być stosowane na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="b8f37-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="b8f37-111">Określa flagi nie poziomu zasad.</span><span class="sxs-lookup"><span data-stu-id="b8f37-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="b8f37-112">Określa, czy zasady mają być stosowane na poziomie wydawcy.</span><span class="sxs-lookup"><span data-stu-id="b8f37-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="b8f37-113">Określa, że zasady powinny mieć zastosowanie na poziomach zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b8f37-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="b8f37-114">Określa, że zasady powinny obsługiwać przenoszenia między implementacjami zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8f37-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="b8f37-115">Zobacz [ \<supportportability — >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) element pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b8f37-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="b8f37-116">Określa, że zasady powinny unified, środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b8f37-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8f37-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8f37-117">Remarks</span></span>  
 <span data-ttu-id="b8f37-118">To wyliczenie jest przekazywany do metody [iclrhostbindingpolicymanager —](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interfejsu, aby określić zmiany w zasadach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b8f37-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8f37-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8f37-119">Requirements</span></span>  
 <span data-ttu-id="b8f37-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8f37-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8f37-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b8f37-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8f37-122">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8f37-122">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b8f37-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b8f37-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8f37-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8f37-124">See also</span></span>

- [<span data-ttu-id="b8f37-125">ICLRAssemblyIdentityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b8f37-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b8f37-126">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b8f37-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
