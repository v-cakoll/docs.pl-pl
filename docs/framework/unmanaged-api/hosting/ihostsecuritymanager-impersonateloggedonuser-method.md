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
ms.openlocfilehash: 6ebf9ad72f7a1b0dd7ac54afa104089182f122ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109892"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="de7a6-102">IHostSecurityManager::ImpersonateLoggedOnUser — Metoda</span><span class="sxs-lookup"><span data-stu-id="de7a6-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="de7a6-103">Żądania, kod można wykonać przy użyciu poświadczeń bieżącej tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="de7a6-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de7a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de7a6-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de7a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de7a6-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="de7a6-106">[in] Token reprezentujący poświadczeń użytkownika do personalizacji.</span><span class="sxs-lookup"><span data-stu-id="de7a6-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de7a6-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="de7a6-107">Return Value</span></span>  
  
|<span data-ttu-id="de7a6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de7a6-108">HRESULT</span></span>|<span data-ttu-id="de7a6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="de7a6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de7a6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="de7a6-110">S_OK</span></span>|`ImpersonateLoggedOnUser` <span data-ttu-id="de7a6-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="de7a6-111">returned successfully.</span></span>|  
|<span data-ttu-id="de7a6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="de7a6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="de7a6-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="de7a6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="de7a6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="de7a6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="de7a6-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="de7a6-115">The call timed out.</span></span>|  
|<span data-ttu-id="de7a6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="de7a6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="de7a6-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="de7a6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="de7a6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="de7a6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="de7a6-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="de7a6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="de7a6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="de7a6-120">E_FAIL</span></span>|<span data-ttu-id="de7a6-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="de7a6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="de7a6-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="de7a6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="de7a6-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="de7a6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de7a6-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de7a6-124">Remarks</span></span>  
 <span data-ttu-id="de7a6-125">Wywołaj `LogonUser` lub powiązanych funkcji Win32, można pobrać uchwytu do poświadczeń bieżącej tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="de7a6-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="de7a6-126">`HANDLE` Typ nie jest zgodny z COM, oznacza to, jego rozmiar jest specyficzne dla systemu operacyjnego i potrzebny organizowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="de7a6-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="de7a6-127">W związku z tym ten token jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.</span><span class="sxs-lookup"><span data-stu-id="de7a6-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de7a6-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de7a6-128">Requirements</span></span>  
 <span data-ttu-id="de7a6-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de7a6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de7a6-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="de7a6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de7a6-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de7a6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="de7a6-132">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="de7a6-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="de7a6-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de7a6-133">See also</span></span>

- [<span data-ttu-id="de7a6-134">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="de7a6-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="de7a6-135">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="de7a6-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="de7a6-136">RevertToSelf, metoda</span><span class="sxs-lookup"><span data-stu-id="de7a6-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
