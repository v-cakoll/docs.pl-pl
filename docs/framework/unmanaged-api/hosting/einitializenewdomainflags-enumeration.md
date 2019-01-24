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
ms.openlocfilehash: 826e02789f6940923538f3e01744345dacf4b2ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705287"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="dcd30-102">EInitializeNewDomainFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="dcd30-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="dcd30-103">Umożliwia hosta zapewnienie środowiska uruchomieniowego informacje dotyczące inicjowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dcd30-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcd30-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="dcd30-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="dcd30-105">Members</span></span>  
  
|<span data-ttu-id="dcd30-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="dcd30-106">Member</span></span>|<span data-ttu-id="dcd30-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dcd30-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="dcd30-108">Bez flag.</span><span class="sxs-lookup"><span data-stu-id="dcd30-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="dcd30-109">Środowisko uruchomieniowe języka wspólnego (CLR) informuje, że host nie wprowadzi zmiany stanu zabezpieczeń domeny aplikacji w <xref:System.AppDomainManager.InitializeNewDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dcd30-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcd30-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcd30-110">Remarks</span></span>  
 <span data-ttu-id="dcd30-111">[Iclrdomainmanager::setappdomainmanagertype —](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) metoda przyjmuje parametr typu `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="dcd30-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcd30-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcd30-112">Requirements</span></span>  
 <span data-ttu-id="dcd30-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcd30-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcd30-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dcd30-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcd30-115">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dcd30-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcd30-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcd30-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd30-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcd30-117">See also</span></span>
- [<span data-ttu-id="dcd30-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="dcd30-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="dcd30-119">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="dcd30-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
