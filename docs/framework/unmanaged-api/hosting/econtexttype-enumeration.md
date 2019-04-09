---
title: EContextType — Wyliczenie
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f3643bf4880532a46fe7f9f57b8077032013728
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118082"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="2eedb-102">EContextType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2eedb-102">EContextType Enumeration</span></span>
<span data-ttu-id="2eedb-103">W tym artykule opisano w kontekście zabezpieczeń aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="2eedb-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eedb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2eedb-104">Syntax</span></span>  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="2eedb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2eedb-105">Members</span></span>  
  
|<span data-ttu-id="2eedb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2eedb-106">Member</span></span>|<span data-ttu-id="2eedb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2eedb-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="2eedb-108">Wskazuje kontekst dla bieżącego wątku w czasie, środowisko uruchomieniowe języka wspólnego (CLR) wywołuje [ihostsecuritymanager::getsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metody lub kontekst wymagane przez środowisko CLR w wywołaniu [ Ihostsecuritymanager::setsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2eedb-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="2eedb-109">Wskazuje kontekst, względem której host ma niższe uprawnienia, takie jak moduł garbage collector lub konstruktory klasę lub moduł.</span><span class="sxs-lookup"><span data-stu-id="2eedb-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eedb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2eedb-110">Remarks</span></span>  
 <span data-ttu-id="2eedb-111">Środowisko CLR zapewnia jedną z `EContextType` wartości jako wartość parametru w wywołaniach `IHostSecurityManager::GetSecurityContext` i `IHostSecurityManager::SetSecurityContext` metody.</span><span class="sxs-lookup"><span data-stu-id="2eedb-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eedb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2eedb-112">Requirements</span></span>  
 <span data-ttu-id="2eedb-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eedb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eedb-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2eedb-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2eedb-115">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2eedb-115">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2eedb-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2eedb-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2eedb-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2eedb-117">See also</span></span>

- [<span data-ttu-id="2eedb-118">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2eedb-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="2eedb-119">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2eedb-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="2eedb-120">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2eedb-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
