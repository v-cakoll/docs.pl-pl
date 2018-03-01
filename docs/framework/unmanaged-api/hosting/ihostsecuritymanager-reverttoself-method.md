---
title: "IHostSecurityManager::RevertToSelf — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 765d40cc99269031093e9241ed1bba6c82b9a042
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="da61a-102">IHostSecurityManager::RevertToSelf — Metoda</span><span class="sxs-lookup"><span data-stu-id="da61a-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="da61a-103">Przerywa personifikacji bieżącej tożsamości użytkownika i zwraca oryginalnego tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="da61a-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da61a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da61a-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="da61a-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="da61a-105">Return Value</span></span>  
  
|<span data-ttu-id="da61a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da61a-106">HRESULT</span></span>|<span data-ttu-id="da61a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="da61a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da61a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="da61a-108">S_OK</span></span>|<span data-ttu-id="da61a-109">`RevertToSelf`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="da61a-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="da61a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da61a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da61a-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="da61a-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da61a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da61a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da61a-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="da61a-113">The call timed out.</span></span>|  
|<span data-ttu-id="da61a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da61a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da61a-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="da61a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da61a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da61a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da61a-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="da61a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da61a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da61a-118">E_FAIL</span></span>|<span data-ttu-id="da61a-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="da61a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da61a-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="da61a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da61a-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="da61a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da61a-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da61a-122">Remarks</span></span>  
 <span data-ttu-id="da61a-123">`RevertToSelf`jest wywoływana, aby wrócić do oryginalnego tokenu wątku, po wcześniejszej wywołanie [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="da61a-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da61a-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da61a-124">Requirements</span></span>  
 <span data-ttu-id="da61a-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da61a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da61a-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="da61a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da61a-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da61a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da61a-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da61a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da61a-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da61a-129">See Also</span></span>  
 [<span data-ttu-id="da61a-130">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="da61a-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="da61a-131">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="da61a-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="da61a-132">ImpersonateLoggedOnUser, metoda</span><span class="sxs-lookup"><span data-stu-id="da61a-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
