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
ms.openlocfilehash: 5e82f542bdc364a52fc558e582134a7d8d554ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131143"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="ee9c8-102">EContextType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ee9c8-102">EContextType Enumeration</span></span>
<span data-ttu-id="ee9c8-103">Opisuje kontekst zabezpieczeń aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="ee9c8-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee9c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee9c8-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="ee9c8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ee9c8-105">Members</span></span>  
  
|<span data-ttu-id="ee9c8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ee9c8-106">Member</span></span>|<span data-ttu-id="ee9c8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ee9c8-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="ee9c8-108">Wskazuje kontekst bieżącego wątku w czasie, gdy środowisko uruchomieniowe języka wspólnego (CLR) wywołuje metodę [IHostSecurityManager:: GetSecurityContext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) lub kontekst żądany przez środowisko CLR w wywołaniu [IHostSecurityManager:: SetSecurityContext — ](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)Metoda.</span><span class="sxs-lookup"><span data-stu-id="ee9c8-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="ee9c8-109">Wskazuje kontekst, w którym host ma niższe uprawnienia, takie jak moduł wyrzucania elementów bezużytecznych lub konstruktory klas lub modułów.</span><span class="sxs-lookup"><span data-stu-id="ee9c8-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee9c8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee9c8-110">Remarks</span></span>  
 <span data-ttu-id="ee9c8-111">Środowisko CLR dostarcza jedną z wartości `EContextType` jako wartość parametru w wywołaniach metody `IHostSecurityManager::GetSecurityContext` i `IHostSecurityManager::SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="ee9c8-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee9c8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee9c8-112">Requirements</span></span>  
 <span data-ttu-id="ee9c8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee9c8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee9c8-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ee9c8-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ee9c8-115">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ee9c8-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee9c8-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee9c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee9c8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee9c8-117">See also</span></span>

- [<span data-ttu-id="ee9c8-118">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee9c8-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="ee9c8-119">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee9c8-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="ee9c8-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ee9c8-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
