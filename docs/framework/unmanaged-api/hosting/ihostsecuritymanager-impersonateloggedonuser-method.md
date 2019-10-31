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
ms.openlocfilehash: 93051ca9a0b6f57f41d0d17335a838fe92832d8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121496"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="bc4c9-102">IHostSecurityManager::ImpersonateLoggedOnUser — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc4c9-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="bc4c9-103">Żąda wykonania kodu przy użyciu poświadczeń bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc4c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc4c9-104">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc4c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc4c9-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="bc4c9-106">podczas Token reprezentujący poświadczenia użytkownika do personifikacji.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc4c9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bc4c9-107">Return Value</span></span>  
  
|<span data-ttu-id="bc4c9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc4c9-108">HRESULT</span></span>|<span data-ttu-id="bc4c9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="bc4c9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc4c9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc4c9-110">S_OK</span></span>|<span data-ttu-id="bc4c9-111">`ImpersonateLoggedOnUser` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="bc4c9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc4c9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc4c9-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bc4c9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bc4c9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bc4c9-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-115">The call timed out.</span></span>|  
|<span data-ttu-id="bc4c9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bc4c9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bc4c9-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bc4c9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bc4c9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bc4c9-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bc4c9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc4c9-120">E_FAIL</span></span>|<span data-ttu-id="bc4c9-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bc4c9-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bc4c9-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc4c9-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc4c9-124">Remarks</span></span>  
 <span data-ttu-id="bc4c9-125">Wywołaj `LogonUser` lub powiązaną funkcję Win32, aby uzyskać dojście do poświadczeń bieżącej tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="bc4c9-126">Typ `HANDLE` nie jest zgodny z modelem COM, oznacza to, że jego rozmiar jest specyficzny dla systemu operacyjnego i wymaga kierowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="bc4c9-127">W ten sposób token jest używany tylko w ramach procesu, między środowiskiem CLR a hostem.</span><span class="sxs-lookup"><span data-stu-id="bc4c9-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc4c9-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc4c9-128">Requirements</span></span>  
 <span data-ttu-id="bc4c9-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc4c9-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc4c9-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bc4c9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc4c9-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bc4c9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc4c9-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc4c9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4c9-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc4c9-133">See also</span></span>

- [<span data-ttu-id="bc4c9-134">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc4c9-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="bc4c9-135">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc4c9-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="bc4c9-136">RevertToSelf, metoda</span><span class="sxs-lookup"><span data-stu-id="bc4c9-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
