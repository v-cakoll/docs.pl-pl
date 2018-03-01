---
title: "EInitializeNewDomainFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa5c9aa050e0f5e634c43080d9caa5011a126529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="9e3c8-102">EInitializeNewDomainFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9e3c8-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="9e3c8-103">Umożliwia hosta zapewnić środowisko uruchomieniowe informacje o inicjowaniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e3c8-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e3c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e3c8-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="9e3c8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9e3c8-105">Members</span></span>  
  
|<span data-ttu-id="9e3c8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9e3c8-106">Member</span></span>|<span data-ttu-id="9e3c8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9e3c8-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="9e3c8-108">Żadnych flag.</span><span class="sxs-lookup"><span data-stu-id="9e3c8-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="9e3c8-109">Środowisko uruchomieniowe języka wspólnego (CLR) informuje, że host nie wprowadzać zmian do stanu zabezpieczeń domeny aplikacji w <xref:System.AppDomainManager.InitializeNewDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9e3c8-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e3c8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e3c8-110">Remarks</span></span>  
 <span data-ttu-id="9e3c8-111">[ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) metoda przyjmuje parametr typu `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="9e3c8-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e3c8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e3c8-112">Requirements</span></span>  
 <span data-ttu-id="9e3c8-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e3c8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e3c8-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e3c8-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e3c8-115">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e3c8-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e3c8-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e3c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e3c8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e3c8-117">See Also</span></span>  
 [<span data-ttu-id="9e3c8-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9e3c8-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="9e3c8-119">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="9e3c8-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
