---
title: IHostSecurityManager::SetThreadToken — Metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e06a76b4d51245388bf36b8127a470f55ca645fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494704"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="ca465-102">IHostSecurityManager::SetThreadToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca465-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="ca465-103">Ustawia obsługi do aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="ca465-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca465-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca465-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca465-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca465-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="ca465-106">[in] Dojście do tokenu, aby ustawić aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="ca465-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca465-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ca465-107">Return Value</span></span>  
  
|<span data-ttu-id="ca465-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca465-108">HRESULT</span></span>|<span data-ttu-id="ca465-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ca465-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca465-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca465-110">S_OK</span></span>|<span data-ttu-id="ca465-111">`SetThreadToken` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="ca465-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="ca465-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca465-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca465-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ca465-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca465-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca465-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca465-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ca465-115">The call timed out.</span></span>|  
|<span data-ttu-id="ca465-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca465-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca465-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="ca465-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca465-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca465-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca465-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ca465-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca465-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca465-120">E_FAIL</span></span>|<span data-ttu-id="ca465-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ca465-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca465-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ca465-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca465-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca465-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca465-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca465-124">Remarks</span></span>  
 <span data-ttu-id="ca465-125">`IHostSecurityManager::SetThreadToken` zachowuje się podobnie do odpowiednich funkcji Win32 o takiej samej nazwie, z tą różnicą, że funkcja Win32 pozwala na obiekt wywołujący, aby przekazać dojścia do dowolnego wątku, podczas gdy `IHostSecurityManager::SetThreadToken` tylko z aktualnie wykonywany Wątek można skojarzyć token.</span><span class="sxs-lookup"><span data-stu-id="ca465-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="ca465-126">`HANDLE` Typ nie jest zgodny z COM; oznacza to, jego rozmiar jest specyficzne dla systemu operacyjnego i potrzebny organizowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="ca465-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="ca465-127">W związku z tym ten token jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.</span><span class="sxs-lookup"><span data-stu-id="ca465-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca465-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca465-128">Requirements</span></span>  
 <span data-ttu-id="ca465-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca465-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca465-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca465-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca465-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca465-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca465-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca465-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca465-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca465-133">See also</span></span>
- [<span data-ttu-id="ca465-134">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca465-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="ca465-135">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca465-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
