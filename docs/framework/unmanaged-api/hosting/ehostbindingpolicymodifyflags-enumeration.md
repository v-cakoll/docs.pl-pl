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
ms.openlocfilehash: 256c362ae0aea51fea16ce799db243b105dee81a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616245"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="e31d0-102">EHostBindingPolicyModifyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e31d0-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="e31d0-103">Umożliwia hostowi określenie typu przekierowania, który powinien być wykonywany przez środowisko uruchomieniowe języka wspólnego (CLR), gdy stosowane są modyfikacje zasad z zestawu źródłowego do zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e31d0-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e31d0-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e31d0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e31d0-105">Members</span></span>  
  
|<span data-ttu-id="e31d0-106">Członek</span><span class="sxs-lookup"><span data-stu-id="e31d0-106">Member</span></span>|<span data-ttu-id="e31d0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e31d0-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="e31d0-108">Określa, że środowisko CLR będzie przeciągać wartości zasad zestawu źródłowego na te, które są określone dla zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e31d0-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="e31d0-109">Określa, że środowisko CLR wykona akcję domyślną.</span><span class="sxs-lookup"><span data-stu-id="e31d0-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="e31d0-110">Określa, że środowisko CLR ustawi wartości z zestawu docelowego na wartości maksymalne.</span><span class="sxs-lookup"><span data-stu-id="e31d0-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="e31d0-111">Określa, że środowisko CLR zamieni wartości zasad zestawu docelowego na te z zestawu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e31d0-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e31d0-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e31d0-112">Remarks</span></span>  
 <span data-ttu-id="e31d0-113">Metoda [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy —](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) przyjmuje parametr typu `EHostBindingPolicyModifyFlags` .</span><span class="sxs-lookup"><span data-stu-id="e31d0-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e31d0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e31d0-114">Requirements</span></span>  
 <span data-ttu-id="e31d0-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e31d0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e31d0-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e31d0-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e31d0-117">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e31d0-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e31d0-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e31d0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e31d0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e31d0-119">See also</span></span>

- [<span data-ttu-id="e31d0-120">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e31d0-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="e31d0-121">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e31d0-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
