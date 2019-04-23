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
ms.openlocfilehash: 04b0d9989d66888c33de0359e4c93529fcfbf8d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095363"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="5dca4-102">EInitializeNewDomainFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5dca4-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="5dca4-103">Umożliwia hosta zapewnienie środowiska uruchomieniowego informacje dotyczące inicjowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5dca4-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dca4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5dca4-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5dca4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5dca4-105">Members</span></span>  
  
|<span data-ttu-id="5dca4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5dca4-106">Member</span></span>|<span data-ttu-id="5dca4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5dca4-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="5dca4-108">Bez flag.</span><span class="sxs-lookup"><span data-stu-id="5dca4-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="5dca4-109">Środowisko uruchomieniowe języka wspólnego (CLR) informuje, że host nie wprowadzi zmiany stanu zabezpieczeń domeny aplikacji w <xref:System.AppDomainManager.InitializeNewDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5dca4-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dca4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5dca4-110">Remarks</span></span>  
 <span data-ttu-id="5dca4-111">[Iclrdomainmanager::setappdomainmanagertype —](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) metoda przyjmuje parametr typu `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="5dca4-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dca4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5dca4-112">Requirements</span></span>  
 <span data-ttu-id="5dca4-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dca4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dca4-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5dca4-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5dca4-115">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5dca4-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5dca4-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dca4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dca4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5dca4-117">See also</span></span>

- [<span data-ttu-id="5dca4-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5dca4-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="5dca4-119">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="5dca4-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
