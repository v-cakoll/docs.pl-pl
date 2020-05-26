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
ms.openlocfilehash: 40857620e47befce361ff8cb04af527915051df3
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804206"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="81e74-102">IHostSecurityContext::Capture — Metoda</span><span class="sxs-lookup"><span data-stu-id="81e74-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="81e74-103">Pobiera klon wystąpienia [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) zwróconego z wywołania [IHostSecurityManager:: GetSecurityContext —](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="81e74-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81e74-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81e74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81e74-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="81e74-106">określoną Wskaźnik na adres klonu `IHostSecurityContext` obiektu do przechwycenia.</span><span class="sxs-lookup"><span data-stu-id="81e74-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81e74-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81e74-107">Return Value</span></span>  
  
|<span data-ttu-id="81e74-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81e74-108">HRESULT</span></span>|<span data-ttu-id="81e74-109">Opis</span><span class="sxs-lookup"><span data-stu-id="81e74-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81e74-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="81e74-110">S_OK</span></span>|<span data-ttu-id="81e74-111">`Capture`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="81e74-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="81e74-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81e74-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81e74-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="81e74-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81e74-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81e74-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81e74-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="81e74-115">The call timed out.</span></span>|  
|<span data-ttu-id="81e74-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81e74-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81e74-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="81e74-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81e74-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81e74-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81e74-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="81e74-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81e74-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81e74-120">E_FAIL</span></span>|<span data-ttu-id="81e74-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="81e74-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81e74-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="81e74-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81e74-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="81e74-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81e74-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81e74-124">Remarks</span></span>  
 <span data-ttu-id="81e74-125">Wskaźnik interfejsu zwrócony z `Capture` jest klonem przechwyconego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="81e74-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="81e74-126">Gdy te informacje są przenoszone przez asynchroniczny punkt kodu, jego okres istnienia jest oddzielony od wskaźnika, z którego wykonano wywołanie.</span><span class="sxs-lookup"><span data-stu-id="81e74-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="81e74-127">Oryginalny wskaźnik może być w związku z tym publikowany.</span><span class="sxs-lookup"><span data-stu-id="81e74-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e74-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81e74-128">Requirements</span></span>  
 <span data-ttu-id="81e74-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81e74-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e74-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81e74-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81e74-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="81e74-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81e74-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e74-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e74-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81e74-133">See also</span></span>

- [<span data-ttu-id="81e74-134">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="81e74-134">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="81e74-135">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="81e74-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
