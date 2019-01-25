---
title: METAHOST_CONFIG_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 961db92c9ca9c713c38469a018ce8cde1fdefdc5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556340"
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="35476-102">METAHOST_CONFIG_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="35476-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="35476-103">W tym artykule opisano możliwe flagi zwracane w `pdwConfigFlags` parametru [iclrmetahostpolicy::getrequestedruntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody, wskazujące na obecność i ustawianie `useLegacyV2RuntimeActivationPolicy` atrybutu w [ \<uruchamiania > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35476-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35476-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35476-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="35476-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="35476-105">Members</span></span>  
  
|<span data-ttu-id="35476-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="35476-106">Member</span></span>|<span data-ttu-id="35476-107">Opis</span><span class="sxs-lookup"><span data-stu-id="35476-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="35476-108">`useLegacyV2RuntimeActivationPolicy` Atrybutu nie była obecna w [ \<uruchamiania > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="35476-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="35476-109">`useLegacyV2RuntimeActivationPolicy` Atrybut jest obecna i ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="35476-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="35476-110">`useLegacyV2RuntimeActivationPolicy` Atrybut jest obecna i ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="35476-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="35476-111">Zastosuj tę maskę do wartości zwracanej w `pdwConfigFlags` można pobrać wartości dotyczą `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="35476-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35476-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35476-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35476-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35476-113">Requirements</span></span>  
 <span data-ttu-id="35476-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35476-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35476-115">**Nagłówek:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="35476-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="35476-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35476-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35476-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35476-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35476-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35476-118">See also</span></span>
- [<span data-ttu-id="35476-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="35476-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="35476-120">GetRequestedRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="35476-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="35476-121">\<Uruchamianie > Element</span><span class="sxs-lookup"><span data-stu-id="35476-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
