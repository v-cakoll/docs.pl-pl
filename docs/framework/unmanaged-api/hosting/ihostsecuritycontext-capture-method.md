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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0f6ae812b64080a2c4d236a2be02ad81c4a11b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193307"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="3017b-102">IHostSecurityContext::Capture — Metoda</span><span class="sxs-lookup"><span data-stu-id="3017b-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="3017b-103">Pobiera klon [ihostsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) wystąpienia zwrócony z wywołania do [ihostsecuritymanager::getsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="3017b-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3017b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3017b-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3017b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3017b-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="3017b-106">[out] Wskaźnik na adres klon `IHostSecurityContext` obiektu do przechwycenia.</span><span class="sxs-lookup"><span data-stu-id="3017b-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3017b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3017b-107">Return Value</span></span>  
  
|<span data-ttu-id="3017b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3017b-108">HRESULT</span></span>|<span data-ttu-id="3017b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3017b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3017b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3017b-110">S_OK</span></span>|<span data-ttu-id="3017b-111">`Capture` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="3017b-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="3017b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3017b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3017b-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="3017b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3017b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3017b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3017b-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="3017b-115">The call timed out.</span></span>|  
|<span data-ttu-id="3017b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3017b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3017b-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="3017b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3017b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3017b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3017b-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="3017b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3017b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3017b-120">E_FAIL</span></span>|<span data-ttu-id="3017b-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3017b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3017b-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="3017b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3017b-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3017b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3017b-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3017b-124">Remarks</span></span>  
 <span data-ttu-id="3017b-125">Wskaźnik interfejsu, zwrócone w wyniku `Capture` jest klonem kontekście przechwyconym.</span><span class="sxs-lookup"><span data-stu-id="3017b-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="3017b-126">Gdy te informacje są przenoszone między punktem kodu asynchronicznego, jego okres istnienia jest oddzielony od, wskaźnika, względem którego rozmowy.</span><span class="sxs-lookup"><span data-stu-id="3017b-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="3017b-127">Oryginalny wskaźnik więc może być zwolnione.</span><span class="sxs-lookup"><span data-stu-id="3017b-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3017b-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3017b-128">Requirements</span></span>  
 <span data-ttu-id="3017b-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3017b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3017b-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3017b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3017b-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3017b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3017b-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3017b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3017b-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3017b-133">See also</span></span>

- [<span data-ttu-id="3017b-134">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="3017b-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="3017b-135">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3017b-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
