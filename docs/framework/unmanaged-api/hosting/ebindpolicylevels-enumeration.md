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
ms.openlocfilehash: 81aef6beb9ee6d622519738d24fdd0a4d42a75b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136550"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="73cf4-102">EBindPolicyLevels — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="73cf4-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="73cf4-103">Zapewnia flagi do określania poziomu, na którym mają być stosowane lub zmodyfikowane zasady zestawu.</span><span class="sxs-lookup"><span data-stu-id="73cf4-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73cf4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73cf4-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="73cf4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="73cf4-105">Members</span></span>  
  
|<span data-ttu-id="73cf4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="73cf4-106">Member</span></span>|<span data-ttu-id="73cf4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="73cf4-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="73cf4-108">Określa, że zasady mają być stosowane na poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="73cf4-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="73cf4-109">Określa, że zasady mają być stosowane na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="73cf4-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="73cf4-110">Określa, że zasady mają być stosowane na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="73cf4-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="73cf4-111">Określa brak flag poziomu zasad.</span><span class="sxs-lookup"><span data-stu-id="73cf4-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="73cf4-112">Określa, że zasady mają być stosowane na poziomie wydawcy.</span><span class="sxs-lookup"><span data-stu-id="73cf4-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="73cf4-113">Określa, że zasady powinny być stosowane na poziomach zmiennych.</span><span class="sxs-lookup"><span data-stu-id="73cf4-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="73cf4-114">Określa, że zasady powinny obsługiwać przenośność między implementacjami zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="73cf4-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="73cf4-115">Zobacz [\<tag supportportability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73cf4-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="73cf4-116">Określa, że zasady powinny być ujednolicone dla tego środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="73cf4-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73cf4-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73cf4-117">Remarks</span></span>  
 <span data-ttu-id="73cf4-118">To wyliczenie jest przesyłane do metod interfejsu [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) , aby określić zmiany zasad aplikacji.</span><span class="sxs-lookup"><span data-stu-id="73cf4-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73cf4-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73cf4-119">Requirements</span></span>  
 <span data-ttu-id="73cf4-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73cf4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73cf4-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="73cf4-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73cf4-122">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="73cf4-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73cf4-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73cf4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cf4-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73cf4-124">See also</span></span>

- [<span data-ttu-id="73cf4-125">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="73cf4-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="73cf4-126">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="73cf4-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
