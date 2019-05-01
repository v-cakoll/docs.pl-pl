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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e8357d20edba993f5a7682f31c04afea4362afd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796061"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="52159-102">EHostBindingPolicyModifyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="52159-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="52159-103">Zezwalaj hostowi na określenie typu przekierowania, których środowisko uruchomieniowe języka wspólnego (CLR), należy wykonać podczas stosowania zmian zasad z zestawu źródłowego zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="52159-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52159-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52159-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="52159-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="52159-105">Members</span></span>  
  
|<span data-ttu-id="52159-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="52159-106">Member</span></span>|<span data-ttu-id="52159-107">Opis</span><span class="sxs-lookup"><span data-stu-id="52159-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="52159-108">Określa, że środowiska CLR będzie łańcucha wartości zasad zestawu źródła na tych dla zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="52159-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="52159-109">Określa, że środowisko CLR wykona domyślne działanie.</span><span class="sxs-lookup"><span data-stu-id="52159-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="52159-110">Określa, czy środowiska CLR będzie równa wartości zasad dla zestawu docelowego maksymalne wartości.</span><span class="sxs-lookup"><span data-stu-id="52159-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="52159-111">Określa środowisko CLR spowoduje zastąpienie wartości zasad dla zestawu docelowego z tymi źródło zestawu.</span><span class="sxs-lookup"><span data-stu-id="52159-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52159-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52159-112">Remarks</span></span>  
 <span data-ttu-id="52159-113">[Iclrhostbindingpolicymanager::modifyapplicationpolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) metoda przyjmuje parametr typu `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="52159-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52159-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52159-114">Requirements</span></span>  
 <span data-ttu-id="52159-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52159-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52159-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52159-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52159-117">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52159-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52159-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52159-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52159-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52159-119">See also</span></span>

- [<span data-ttu-id="52159-120">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="52159-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="52159-121">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="52159-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
