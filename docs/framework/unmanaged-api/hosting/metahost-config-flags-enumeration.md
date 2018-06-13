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
ms.openlocfilehash: a13897f71bb675b982a84d57d310b799989c41aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442933"
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="fcb6e-102">METAHOST_CONFIG_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fcb6e-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="fcb6e-103">W tym artykule opisano możliwe flagi zwracane w `pdwConfigFlags` parametr [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody, wskazujące na obecność i ustawienie `useLegacyV2RuntimeActivationPolicy` atrybutu w [ \<uruchamiania > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fcb6e-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcb6e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcb6e-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="fcb6e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fcb6e-105">Members</span></span>  
  
|<span data-ttu-id="fcb6e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fcb6e-106">Member</span></span>|<span data-ttu-id="fcb6e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fcb6e-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="fcb6e-108">`useLegacyV2RuntimeActivationPolicy` Atrybutu nie była obecna w [ \<uruchamiania > elementu](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="fcb6e-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="fcb6e-109">`useLegacyV2RuntimeActivationPolicy` Atrybut był obecny i ustaw do `true`.</span><span class="sxs-lookup"><span data-stu-id="fcb6e-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="fcb6e-110">`useLegacyV2RuntimeActivationPolicy` Atrybut był obecny i ustaw do `false`.</span><span class="sxs-lookup"><span data-stu-id="fcb6e-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="fcb6e-111">Zastosuj tę maskę wartość zwracana w `pdwConfigFlags` można pobrać wartości odpowiadających `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="fcb6e-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcb6e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fcb6e-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcb6e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fcb6e-113">Requirements</span></span>  
 <span data-ttu-id="fcb6e-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcb6e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcb6e-115">**Nagłówek:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="fcb6e-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="fcb6e-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fcb6e-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcb6e-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcb6e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcb6e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcb6e-118">See Also</span></span>  
 [<span data-ttu-id="fcb6e-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fcb6e-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="fcb6e-120">GetRequestedRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="fcb6e-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)  
 [<span data-ttu-id="fcb6e-121">\<Uruchamianie > — Element</span><span class="sxs-lookup"><span data-stu-id="fcb6e-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
