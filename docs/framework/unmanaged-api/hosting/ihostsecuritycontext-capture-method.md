---
title: IHostSecurityContext::Capture — Metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
ms.openlocfilehash: 96bb3a530bf4c63c3662ecfa635a929381fc0de6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121538"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="f82b3-102">IHostSecurityContext::Capture — Metoda</span><span class="sxs-lookup"><span data-stu-id="f82b3-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="f82b3-103">Pobiera klon wystąpienia [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) zwróconego z wywołania [IHostSecurityManager:: GetSecurityContext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="f82b3-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f82b3-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f82b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f82b3-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="f82b3-106">określoną Wskaźnik na adres klonu obiektu `IHostSecurityContext`, który ma zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="f82b3-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f82b3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f82b3-107">Return Value</span></span>  
  
|<span data-ttu-id="f82b3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f82b3-108">HRESULT</span></span>|<span data-ttu-id="f82b3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f82b3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f82b3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f82b3-110">S_OK</span></span>|<span data-ttu-id="f82b3-111">`Capture` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="f82b3-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="f82b3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f82b3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f82b3-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f82b3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f82b3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f82b3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f82b3-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f82b3-115">The call timed out.</span></span>|  
|<span data-ttu-id="f82b3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f82b3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f82b3-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f82b3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f82b3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f82b3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f82b3-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="f82b3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f82b3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f82b3-120">E_FAIL</span></span>|<span data-ttu-id="f82b3-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f82b3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f82b3-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="f82b3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f82b3-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f82b3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f82b3-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f82b3-124">Remarks</span></span>  
 <span data-ttu-id="f82b3-125">Wskaźnik interfejsu zwrócony z `Capture` jest klonem przechwyconego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="f82b3-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="f82b3-126">Gdy te informacje są przenoszone przez asynchroniczny punkt kodu, jego okres istnienia jest oddzielony od wskaźnika, z którego wykonano wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f82b3-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="f82b3-127">Oryginalny wskaźnik może być w związku z tym publikowany.</span><span class="sxs-lookup"><span data-stu-id="f82b3-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f82b3-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f82b3-128">Requirements</span></span>  
 <span data-ttu-id="f82b3-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f82b3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f82b3-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f82b3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f82b3-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f82b3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f82b3-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82b3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82b3-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f82b3-133">See also</span></span>

- [<span data-ttu-id="f82b3-134">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="f82b3-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="f82b3-135">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f82b3-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
