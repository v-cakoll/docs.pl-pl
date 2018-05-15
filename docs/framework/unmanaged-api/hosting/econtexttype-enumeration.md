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
ms.openlocfilehash: 7a261d9164e8714531eab1fe9fc8148304e6d5bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="d3c7d-102">EContextType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d3c7d-102">EContextType Enumeration</span></span>
<span data-ttu-id="d3c7d-103">W tym artykule opisano wątku aktualnie wykonywane w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d3c7d-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3c7d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3c7d-104">Syntax</span></span>  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="d3c7d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d3c7d-105">Members</span></span>  
  
|<span data-ttu-id="d3c7d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d3c7d-106">Member</span></span>|<span data-ttu-id="d3c7d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d3c7d-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="d3c7d-108">Wskazuje kontekstu w bieżącym wątku w momencie wywołania środowisko uruchomieniowe języka wspólnego (CLR) [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metody lub kontekstu żądanego przez środowisko CLR w wywołaniu [ IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d3c7d-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="d3c7d-109">Wskazuje kontekst, w odniesieniu do której host ma niższe uprawnienia, takie jak moduł zbierający elementy bezużyteczne lub klasę lub moduł konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="d3c7d-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3c7d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3c7d-110">Remarks</span></span>  
 <span data-ttu-id="d3c7d-111">Środowisko CLR udostępnia jeden z `EContextType` wartości jako wartości parametru w wywołaniach `IHostSecurityManager::GetSecurityContext` i `IHostSecurityManager::SetSecurityContext` metody.</span><span class="sxs-lookup"><span data-stu-id="d3c7d-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3c7d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3c7d-112">Requirements</span></span>  
 <span data-ttu-id="d3c7d-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3c7d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3c7d-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3c7d-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3c7d-115">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3c7d-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3c7d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3c7d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c7d-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3c7d-117">See Also</span></span>  
 [<span data-ttu-id="d3c7d-118">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3c7d-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="d3c7d-119">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3c7d-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="d3c7d-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d3c7d-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
