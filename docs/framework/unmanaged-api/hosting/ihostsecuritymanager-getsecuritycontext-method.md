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
ms.openlocfilehash: 7198698edce48546c4f9a82ace18d5a6e71891ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176256"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="9e4e2-102">IHostSecurityManager::GetSecurityContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e4e2-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="9e4e2-103">Pobiera żądany [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e4e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e4e2-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e4e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e4e2-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="9e4e2-106">[w] Jedna z wartości [EContextType,](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) wskazująca, jaki typ kontekstu zabezpieczeń zwrócić.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="9e4e2-107">[na zewnątrz] Adres wskaźnika interfejsu do `IHostSecurityContext` `eContextType`pliku .</span><span class="sxs-lookup"><span data-stu-id="9e4e2-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e4e2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9e4e2-108">Return Value</span></span>  
  
|<span data-ttu-id="9e4e2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e4e2-109">HRESULT</span></span>|<span data-ttu-id="9e4e2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9e4e2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e4e2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e4e2-111">S_OK</span></span>|<span data-ttu-id="9e4e2-112">`GetSecurityContext`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="9e4e2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e4e2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e4e2-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e4e2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e4e2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e4e2-116">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-116">The call timed out.</span></span>|  
|<span data-ttu-id="9e4e2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e4e2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e4e2-118">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e4e2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e4e2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e4e2-120">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e4e2-121">E_fail</span><span class="sxs-lookup"><span data-stu-id="9e4e2-121">E_FAIL</span></span>|<span data-ttu-id="9e4e2-122">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e4e2-123">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e4e2-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e4e2-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e4e2-125">Remarks</span></span>  
 <span data-ttu-id="9e4e2-126">Host może kontrolować dostęp do kodu tokenów wątku za pomocą kodu CLR i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="9e4e2-127">Można również zapewnić, że pełne informacje kontekstu zabezpieczeń są przekazywane przez operacje asynchroniczne lub punkty kodu z ograniczonym dostępem do kodu.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="9e4e2-128">`IHostSecurityContext`hermetyzuje te informacje kontekstu zabezpieczeń, który jest nieprzezroczysty dla CLR.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="9e4e2-129">CLR przechwytuje te informacje i przenosi go między puli wątków towarów roboczych wysyłki, wykonanie finalizatora i modułu i konstrukcji klasy.</span><span class="sxs-lookup"><span data-stu-id="9e4e2-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e4e2-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e4e2-130">Requirements</span></span>  
 <span data-ttu-id="9e4e2-131">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e4e2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e4e2-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e4e2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e4e2-133">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e4e2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e4e2-134">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e4e2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4e2-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e4e2-135">See also</span></span>

- [<span data-ttu-id="9e4e2-136">EContextType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9e4e2-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="9e4e2-137">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9e4e2-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="9e4e2-138">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e4e2-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
