---
title: EHostBindingPolicyModifyFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: a2faf22b48dd0b809d6c3668a37f2119733a9b18
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129446"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="e4731-102">EHostBindingPolicyModifyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e4731-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="e4731-103">Umożliwia hostowi określenie typu przekierowania, który powinien być wykonywany przez środowisko uruchomieniowe języka wspólnego (CLR), gdy stosowane są modyfikacje zasad z zestawu źródłowego do zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e4731-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4731-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4731-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e4731-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e4731-105">Members</span></span>  
  
|<span data-ttu-id="e4731-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e4731-106">Member</span></span>|<span data-ttu-id="e4731-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e4731-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="e4731-108">Określa, że środowisko CLR będzie przeciągać wartości zasad zestawu źródłowego na te, które są określone dla zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e4731-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="e4731-109">Określa, że środowisko CLR wykona akcję domyślną.</span><span class="sxs-lookup"><span data-stu-id="e4731-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="e4731-110">Określa, że środowisko CLR ustawi wartości z zestawu docelowego na wartości maksymalne.</span><span class="sxs-lookup"><span data-stu-id="e4731-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="e4731-111">Określa, że środowisko CLR zamieni wartości zasad zestawu docelowego na te z zestawu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e4731-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4731-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4731-112">Remarks</span></span>  
 <span data-ttu-id="e4731-113">Metoda [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) przyjmuje parametr typu `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="e4731-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4731-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4731-114">Requirements</span></span>  
 <span data-ttu-id="e4731-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4731-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4731-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4731-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4731-117">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4731-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4731-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4731-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4731-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4731-119">See also</span></span>

- [<span data-ttu-id="e4731-120">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4731-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="e4731-121">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e4731-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
