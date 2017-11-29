---
title: "IHostSecurityManager::ImpersonateLoggedOnUser — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.ImpersonateLoggedOnUser
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c5956dcad6908f0117de7f5ff0c6632ad3bb925
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="62e52-102">IHostSecurityManager::ImpersonateLoggedOnUser — Metoda</span><span class="sxs-lookup"><span data-stu-id="62e52-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="62e52-103">Żądania który kodu można wykonać przy użyciu poświadczeń Bieżąca tożsamość użytkownika.</span><span class="sxs-lookup"><span data-stu-id="62e52-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62e52-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62e52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62e52-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="62e52-106">[in] Token reprezentujący poświadczeń użytkownika do personalizacji.</span><span class="sxs-lookup"><span data-stu-id="62e52-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62e52-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="62e52-107">Return Value</span></span>  
  
|<span data-ttu-id="62e52-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62e52-108">HRESULT</span></span>|<span data-ttu-id="62e52-109">Opis</span><span class="sxs-lookup"><span data-stu-id="62e52-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62e52-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="62e52-110">S_OK</span></span>|<span data-ttu-id="62e52-111">`ImpersonateLoggedOnUser`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="62e52-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="62e52-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="62e52-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="62e52-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="62e52-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="62e52-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="62e52-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="62e52-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="62e52-115">The call timed out.</span></span>|  
|<span data-ttu-id="62e52-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="62e52-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="62e52-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="62e52-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="62e52-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="62e52-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="62e52-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="62e52-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="62e52-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62e52-120">E_FAIL</span></span>|<span data-ttu-id="62e52-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="62e52-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="62e52-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="62e52-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="62e52-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="62e52-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62e52-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62e52-124">Remarks</span></span>  
 <span data-ttu-id="62e52-125">Wywołanie `LogonUser` lub powiązanych funkcji Win32 uzyskać dojścia do poświadczeń Bieżąca tożsamość użytkownika.</span><span class="sxs-lookup"><span data-stu-id="62e52-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="62e52-126">`HANDLE` Typ nie jest zgodny z interfejsem COM, oznacza to, jego rozmiar jest specyficzna dla systemu operacyjnego i wymaga przekazywanie niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="62e52-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="62e52-127">W związku z tym token ten jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.</span><span class="sxs-lookup"><span data-stu-id="62e52-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62e52-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62e52-128">Requirements</span></span>  
 <span data-ttu-id="62e52-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62e52-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62e52-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62e52-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62e52-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62e52-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62e52-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62e52-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e52-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62e52-133">See Also</span></span>  
 [<span data-ttu-id="62e52-134">IHostSecurityContext — interfejs</span><span class="sxs-lookup"><span data-stu-id="62e52-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="62e52-135">IHostSecurityManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="62e52-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="62e52-136">RevertToSelf — metoda</span><span class="sxs-lookup"><span data-stu-id="62e52-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
