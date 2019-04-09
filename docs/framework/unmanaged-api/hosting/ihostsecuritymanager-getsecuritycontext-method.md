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
ms.openlocfilehash: 1f4f923e868b72e9de33884e4814ebfa329a16e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105836"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="d9f8f-102">IHostSecurityManager::GetSecurityContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9f8f-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="d9f8f-103">Pobiera żądany [ihostsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9f8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9f8f-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9f8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9f8f-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="d9f8f-106">[in] Jedną z [econtexttype —](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) wartości, wskazujący typ kontekstu zabezpieczeń do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="d9f8f-107">[out] Adres wskaźnika interfejsu do `IHostSecurityContext` z `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9f8f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d9f8f-108">Return Value</span></span>  
  
|<span data-ttu-id="d9f8f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9f8f-109">HRESULT</span></span>|<span data-ttu-id="d9f8f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d9f8f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9f8f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9f8f-111">S_OK</span></span>|`GetSecurityContext` <span data-ttu-id="d9f8f-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-112">returned successfully.</span></span>|  
|<span data-ttu-id="d9f8f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9f8f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9f8f-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9f8f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9f8f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9f8f-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-116">The call timed out.</span></span>|  
|<span data-ttu-id="d9f8f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9f8f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9f8f-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9f8f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9f8f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9f8f-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9f8f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9f8f-121">E_FAIL</span></span>|<span data-ttu-id="d9f8f-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9f8f-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9f8f-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9f8f-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9f8f-125">Remarks</span></span>  
 <span data-ttu-id="d9f8f-126">Hosta można kontrolować wszelki dostęp kodu do tokenów wątku przez kod CLR i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="d9f8f-127">Można to także zapewnić pełne zabezpieczenia informacji kontekstowych jest przekazywany w operacji asynchronicznych lub punkty kodowe dostęp ograniczony kod.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> `IHostSecurityContext` <span data-ttu-id="d9f8f-128">hermetyzuje informacje kontekstu zabezpieczeń, która jest nieprzezroczysta dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-128">encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="d9f8f-129">Środowisko CLR rejestruje te informacje i przenosi ją wątek puli procesów roboczych elementu wysyłania, wykonanie finalizator i konstruowania modułu i klasy.</span><span class="sxs-lookup"><span data-stu-id="d9f8f-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9f8f-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9f8f-130">Requirements</span></span>  
 <span data-ttu-id="d9f8f-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9f8f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9f8f-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9f8f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9f8f-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9f8f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d9f8f-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d9f8f-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9f8f-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9f8f-135">See also</span></span>

- [<span data-ttu-id="d9f8f-136">EContextType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d9f8f-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="d9f8f-137">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d9f8f-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="d9f8f-138">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d9f8f-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
