---
title: IHostSecurityManager::RevertToSelf — Metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d282f6d37a2be8a41f4fbda579b3b467b9bfc8ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120071"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="cc166-102">IHostSecurityManager::RevertToSelf — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc166-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="cc166-103">Kończy działanie personifikacji bieżącej tożsamości użytkownika, a następnie zwraca oryginalny tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="cc166-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc166-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc166-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cc166-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cc166-105">Return Value</span></span>  
  
|<span data-ttu-id="cc166-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc166-106">HRESULT</span></span>|<span data-ttu-id="cc166-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cc166-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc166-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc166-108">S_OK</span></span>|`RevertToSelf` <span data-ttu-id="cc166-109">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="cc166-109">returned successfully.</span></span>|  
|<span data-ttu-id="cc166-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc166-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc166-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="cc166-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc166-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc166-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc166-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="cc166-113">The call timed out.</span></span>|  
|<span data-ttu-id="cc166-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc166-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc166-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="cc166-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc166-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc166-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc166-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="cc166-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc166-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc166-118">E_FAIL</span></span>|<span data-ttu-id="cc166-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cc166-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc166-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="cc166-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc166-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc166-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc166-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc166-122">Remarks</span></span>  
 `RevertToSelf` <span data-ttu-id="cc166-123">jest wywoływana, aby powrócić do oryginalnego tokenu wątku po wcześniejszym wywołaniem [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="cc166-123">is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc166-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc166-124">Requirements</span></span>  
 <span data-ttu-id="cc166-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc166-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc166-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc166-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc166-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc166-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cc166-128">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cc166-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cc166-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc166-129">See also</span></span>

- [<span data-ttu-id="cc166-130">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cc166-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="cc166-131">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cc166-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="cc166-132">ImpersonateLoggedOnUser, metoda</span><span class="sxs-lookup"><span data-stu-id="cc166-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
