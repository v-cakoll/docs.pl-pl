---
title: EInitializeNewDomainFlags — Wyliczenie
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0175ab1d06a8166a5bbfd0c42018085a801740f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431452"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="bbd7e-102">EInitializeNewDomainFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bbd7e-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="bbd7e-103">Umożliwia hosta zapewnić środowisko uruchomieniowe informacje o inicjowaniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbd7e-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbd7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbd7e-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bbd7e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bbd7e-105">Members</span></span>  
  
|<span data-ttu-id="bbd7e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bbd7e-106">Member</span></span>|<span data-ttu-id="bbd7e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bbd7e-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="bbd7e-108">Żadnych flag.</span><span class="sxs-lookup"><span data-stu-id="bbd7e-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="bbd7e-109">Środowisko uruchomieniowe języka wspólnego (CLR) informuje, że host nie wprowadzać zmian do stanu zabezpieczeń domeny aplikacji w <xref:System.AppDomainManager.InitializeNewDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bbd7e-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbd7e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbd7e-110">Remarks</span></span>  
 <span data-ttu-id="bbd7e-111">[ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) metoda przyjmuje parametr typu `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="bbd7e-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbd7e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbd7e-112">Requirements</span></span>  
 <span data-ttu-id="bbd7e-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbd7e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbd7e-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bbd7e-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbd7e-115">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bbd7e-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbd7e-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbd7e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd7e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbd7e-117">See Also</span></span>  
 [<span data-ttu-id="bbd7e-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="bbd7e-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="bbd7e-119">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="bbd7e-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
