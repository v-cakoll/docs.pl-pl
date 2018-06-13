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
ms.openlocfilehash: dc57c9465bfafde17156eeec65e52d65c8af9038
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439988"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="f1b8e-102">IHostSecurityManager::ImpersonateLoggedOnUser — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1b8e-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="f1b8e-103">Żądania który kodu można wykonać przy użyciu poświadczeń Bieżąca tożsamość użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1b8e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1b8e-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1b8e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1b8e-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="f1b8e-106">[in] Token reprezentujący poświadczeń użytkownika do personalizacji.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1b8e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f1b8e-107">Return Value</span></span>  
  
|<span data-ttu-id="f1b8e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1b8e-108">HRESULT</span></span>|<span data-ttu-id="f1b8e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f1b8e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1b8e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1b8e-110">S_OK</span></span>|<span data-ttu-id="f1b8e-111">`ImpersonateLoggedOnUser` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="f1b8e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f1b8e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f1b8e-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f1b8e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f1b8e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f1b8e-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-115">The call timed out.</span></span>|  
|<span data-ttu-id="f1b8e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1b8e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f1b8e-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f1b8e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f1b8e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f1b8e-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f1b8e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f1b8e-120">E_FAIL</span></span>|<span data-ttu-id="f1b8e-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f1b8e-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f1b8e-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1b8e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1b8e-124">Remarks</span></span>  
 <span data-ttu-id="f1b8e-125">Wywołanie `LogonUser` lub powiązanych funkcji Win32 uzyskać dojścia do poświadczeń Bieżąca tożsamość użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="f1b8e-126">`HANDLE` Typ nie jest zgodny z interfejsem COM, oznacza to, jego rozmiar jest specyficzna dla systemu operacyjnego i wymaga przekazywanie niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="f1b8e-127">W związku z tym token ten jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.</span><span class="sxs-lookup"><span data-stu-id="f1b8e-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1b8e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1b8e-128">Requirements</span></span>  
 <span data-ttu-id="f1b8e-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1b8e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1b8e-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f1b8e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1b8e-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1b8e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1b8e-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1b8e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b8e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1b8e-133">See Also</span></span>  
 [<span data-ttu-id="f1b8e-134">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1b8e-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="f1b8e-135">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1b8e-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="f1b8e-136">RevertToSelf, metoda</span><span class="sxs-lookup"><span data-stu-id="f1b8e-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
