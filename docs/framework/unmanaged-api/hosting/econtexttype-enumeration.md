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
ms.openlocfilehash: b93b27957cc715a5b4718dd9ef61cd11f4a39914
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493422"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="15821-102">EContextType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="15821-102">EContextType Enumeration</span></span>
<span data-ttu-id="15821-103">Opisuje kontekst zabezpieczeń aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="15821-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15821-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15821-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="15821-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="15821-105">Members</span></span>  
  
|<span data-ttu-id="15821-106">Członek</span><span class="sxs-lookup"><span data-stu-id="15821-106">Member</span></span>|<span data-ttu-id="15821-107">Opis</span><span class="sxs-lookup"><span data-stu-id="15821-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="15821-108">Wskazuje kontekst bieżącego wątku w czasie, gdy środowisko uruchomieniowe języka wspólnego (CLR) wywołuje metodę [IHostSecurityManager:: GetSecurityContext —](ihostsecuritymanager-getsecuritycontext-method.md) lub kontekst żądany przez środowisko CLR w wywołaniu metody [IHostSecurityManager:: SetSecurityContext —](ihostsecuritymanager-setsecuritycontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="15821-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="15821-109">Wskazuje kontekst, w którym host ma niższe uprawnienia, takie jak moduł wyrzucania elementów bezużytecznych lub konstruktory klas lub modułów.</span><span class="sxs-lookup"><span data-stu-id="15821-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15821-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15821-110">Remarks</span></span>  
 <span data-ttu-id="15821-111">Środowisko CLR dostarcza jedną z `EContextType` wartości jako wartość parametru w wywołaniach `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` metod i.</span><span class="sxs-lookup"><span data-stu-id="15821-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15821-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15821-112">Requirements</span></span>  
 <span data-ttu-id="15821-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15821-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15821-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="15821-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15821-115">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="15821-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15821-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15821-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15821-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15821-117">See also</span></span>

- [<span data-ttu-id="15821-118">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="15821-118">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="15821-119">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="15821-119">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="15821-120">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="15821-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
