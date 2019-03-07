---
title: IHostSecurityManager::GetSecurityContext — Metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d17609e585f6e0ecd685d893bb0f8b3e4c0fe0cc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484835"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="ac081-102">IHostSecurityManager::GetSecurityContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac081-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="ac081-103">Pobiera żądany [ihostsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.</span><span class="sxs-lookup"><span data-stu-id="ac081-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac081-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac081-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac081-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac081-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="ac081-106">[in] Jedną z [econtexttype —](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) wartości, wskazujący typ kontekstu zabezpieczeń do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="ac081-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="ac081-107">[out] Adres wskaźnika interfejsu do `IHostSecurityContext` z `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="ac081-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac081-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ac081-108">Return Value</span></span>  
  
|<span data-ttu-id="ac081-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac081-109">HRESULT</span></span>|<span data-ttu-id="ac081-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ac081-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac081-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac081-111">S_OK</span></span>|<span data-ttu-id="ac081-112">`GetSecurityContext` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="ac081-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="ac081-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac081-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac081-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ac081-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac081-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac081-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac081-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ac081-116">The call timed out.</span></span>|  
|<span data-ttu-id="ac081-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac081-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac081-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="ac081-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac081-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac081-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac081-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ac081-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac081-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac081-121">E_FAIL</span></span>|<span data-ttu-id="ac081-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ac081-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac081-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ac081-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac081-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ac081-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac081-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac081-125">Remarks</span></span>  
 <span data-ttu-id="ac081-126">Hosta można kontrolować wszelki dostęp kodu do tokenów wątku przez kod CLR i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ac081-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="ac081-127">Można to także zapewnić pełne zabezpieczenia informacji kontekstowych jest przekazywany w operacji asynchronicznych lub punkty kodowe dostęp ograniczony kod.</span><span class="sxs-lookup"><span data-stu-id="ac081-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="ac081-128">`IHostSecurityContext` hermetyzuje informacje kontekstu zabezpieczeń, która jest nieprzezroczysta dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ac081-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="ac081-129">Środowisko CLR rejestruje te informacje i przenosi ją wątek puli procesów roboczych elementu wysyłania, wykonanie finalizator i konstruowania modułu i klasy.</span><span class="sxs-lookup"><span data-stu-id="ac081-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac081-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac081-130">Requirements</span></span>  
 <span data-ttu-id="ac081-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac081-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac081-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac081-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac081-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac081-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac081-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac081-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac081-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac081-135">See also</span></span>
- [<span data-ttu-id="ac081-136">EContextType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ac081-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="ac081-137">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac081-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="ac081-138">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac081-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
