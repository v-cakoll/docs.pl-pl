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
ms.openlocfilehash: c34d9243e4ed7ed2492784154b157189c7d22cd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="a839b-102">IHostSecurityManager::RevertToSelf — Metoda</span><span class="sxs-lookup"><span data-stu-id="a839b-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="a839b-103">Przerywa personifikacji bieżącej tożsamości użytkownika i zwraca oryginalnego tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="a839b-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a839b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a839b-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a839b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a839b-105">Return Value</span></span>  
  
|<span data-ttu-id="a839b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a839b-106">HRESULT</span></span>|<span data-ttu-id="a839b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a839b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a839b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a839b-108">S_OK</span></span>|<span data-ttu-id="a839b-109">`RevertToSelf` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a839b-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="a839b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a839b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a839b-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a839b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a839b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a839b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a839b-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a839b-113">The call timed out.</span></span>|  
|<span data-ttu-id="a839b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a839b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a839b-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a839b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a839b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a839b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a839b-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a839b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a839b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a839b-118">E_FAIL</span></span>|<span data-ttu-id="a839b-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a839b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a839b-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a839b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a839b-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a839b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a839b-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a839b-122">Remarks</span></span>  
 <span data-ttu-id="a839b-123">`RevertToSelf` jest wywoływana, aby wrócić do oryginalnego tokenu wątku, po wcześniejszej wywołanie [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a839b-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a839b-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a839b-124">Requirements</span></span>  
 <span data-ttu-id="a839b-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a839b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a839b-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a839b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a839b-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a839b-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a839b-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a839b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a839b-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a839b-129">See Also</span></span>  
 [<span data-ttu-id="a839b-130">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="a839b-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="a839b-131">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a839b-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="a839b-132">ImpersonateLoggedOnUser, metoda</span><span class="sxs-lookup"><span data-stu-id="a839b-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
