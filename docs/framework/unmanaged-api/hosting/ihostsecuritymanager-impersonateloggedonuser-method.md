---
title: IHostSecurityManager::ImpersonateLoggedOnUser — Metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e4a90e8cd50ef1b3324aed35ae5cc34225bb2f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471358"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="8af7e-102">IHostSecurityManager::ImpersonateLoggedOnUser — Metoda</span><span class="sxs-lookup"><span data-stu-id="8af7e-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="8af7e-103">Żądania, kod można wykonać przy użyciu poświadczeń bieżącej tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8af7e-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8af7e-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8af7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8af7e-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="8af7e-106">[in] Token reprezentujący poświadczeń użytkownika do personalizacji.</span><span class="sxs-lookup"><span data-stu-id="8af7e-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8af7e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8af7e-107">Return Value</span></span>  
  
|<span data-ttu-id="8af7e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8af7e-108">HRESULT</span></span>|<span data-ttu-id="8af7e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8af7e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8af7e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8af7e-110">S_OK</span></span>|<span data-ttu-id="8af7e-111">`ImpersonateLoggedOnUser` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="8af7e-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="8af7e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8af7e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8af7e-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8af7e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8af7e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8af7e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8af7e-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="8af7e-115">The call timed out.</span></span>|  
|<span data-ttu-id="8af7e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8af7e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8af7e-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="8af7e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8af7e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8af7e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8af7e-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="8af7e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8af7e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8af7e-120">E_FAIL</span></span>|<span data-ttu-id="8af7e-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8af7e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8af7e-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8af7e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8af7e-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8af7e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8af7e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8af7e-124">Remarks</span></span>  
 <span data-ttu-id="8af7e-125">Wywołaj `LogonUser` lub powiązanych funkcji Win32, można pobrać uchwytu do poświadczeń bieżącej tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8af7e-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="8af7e-126">`HANDLE` Typ nie jest zgodny z COM, oznacza to, jego rozmiar jest specyficzne dla systemu operacyjnego i potrzebny organizowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="8af7e-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="8af7e-127">W związku z tym ten token jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.</span><span class="sxs-lookup"><span data-stu-id="8af7e-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8af7e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8af7e-128">Requirements</span></span>  
 <span data-ttu-id="8af7e-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8af7e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8af7e-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8af7e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8af7e-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8af7e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8af7e-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8af7e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af7e-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8af7e-133">See also</span></span>
- [<span data-ttu-id="8af7e-134">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="8af7e-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="8af7e-135">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8af7e-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="8af7e-136">RevertToSelf, metoda</span><span class="sxs-lookup"><span data-stu-id="8af7e-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
