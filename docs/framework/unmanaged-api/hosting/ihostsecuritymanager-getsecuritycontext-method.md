---
title: "IHostSecurityManager::GetSecurityContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.GetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a5fcdf0d0244694a52cf1964d0e7c4be692df2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="e3a82-102">IHostSecurityManager::GetSecurityContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3a82-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="e3a82-103">Pobiera żądanie [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.</span><span class="sxs-lookup"><span data-stu-id="e3a82-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3a82-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3a82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3a82-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="e3a82-106">[in] Jeden z [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) wartości, wskazującą, jaki typ kontekstu zabezpieczeń do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="e3a82-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="e3a82-107">[out] Adres wskaźnika interfejsu do `IHostSecurityContext` z `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="e3a82-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3a82-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3a82-108">Return Value</span></span>  
  
|<span data-ttu-id="e3a82-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3a82-109">HRESULT</span></span>|<span data-ttu-id="e3a82-110">Opis</span><span class="sxs-lookup"><span data-stu-id="e3a82-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3a82-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3a82-111">S_OK</span></span>|<span data-ttu-id="e3a82-112">`GetSecurityContext`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e3a82-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="e3a82-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e3a82-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e3a82-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e3a82-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e3a82-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e3a82-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e3a82-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e3a82-116">The call timed out.</span></span>|  
|<span data-ttu-id="e3a82-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3a82-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e3a82-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e3a82-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e3a82-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e3a82-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e3a82-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e3a82-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e3a82-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e3a82-121">E_FAIL</span></span>|<span data-ttu-id="e3a82-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e3a82-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e3a82-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e3a82-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e3a82-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e3a82-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3a82-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3a82-125">Remarks</span></span>  
 <span data-ttu-id="e3a82-126">Hosta można kontrolować kod dostęp do tokenów wątku przez kod zarówno CLR, jak i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e3a82-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="e3a82-127">Zapewnia również Zabezpieczenia pełne informacje o kontekście jest przekazywany przez operacje asynchroniczne lub punktów kodowych z ograniczeniami kod dostępu.</span><span class="sxs-lookup"><span data-stu-id="e3a82-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="e3a82-128">`IHostSecurityContext`hermetyzuje informacje kontekstu zabezpieczeń, które jest nieprzezroczysta dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="e3a82-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="e3a82-129">Środowisko CLR przechwytuje informacje i przenosi ją wysyłania elementu roboczego puli wątków, wykonanie finalizatora i budowy modułu i klasy.</span><span class="sxs-lookup"><span data-stu-id="e3a82-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3a82-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3a82-130">Requirements</span></span>  
 <span data-ttu-id="e3a82-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3a82-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3a82-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e3a82-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3a82-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3a82-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3a82-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3a82-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a82-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3a82-135">See Also</span></span>  
 [<span data-ttu-id="e3a82-136">EContextType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e3a82-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="e3a82-137">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3a82-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="e3a82-138">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3a82-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
