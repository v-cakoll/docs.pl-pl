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
ms.openlocfilehash: 3aabc21eb15479fe81c922c3fe9625b210caa9d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778001"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="34879-102">IHostSecurityManager::SetThreadToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="34879-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="34879-103">Ustawia obsługi do aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="34879-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34879-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34879-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34879-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34879-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="34879-106">[in] Dojście do tokenu, aby ustawić aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="34879-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34879-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="34879-107">Return Value</span></span>  
  
|<span data-ttu-id="34879-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34879-108">HRESULT</span></span>|<span data-ttu-id="34879-109">Opis</span><span class="sxs-lookup"><span data-stu-id="34879-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34879-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="34879-110">S_OK</span></span>|<span data-ttu-id="34879-111">`SetThreadToken` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="34879-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="34879-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34879-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34879-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="34879-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34879-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34879-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34879-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="34879-115">The call timed out.</span></span>|  
|<span data-ttu-id="34879-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34879-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34879-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="34879-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34879-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34879-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34879-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="34879-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34879-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34879-120">E_FAIL</span></span>|<span data-ttu-id="34879-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="34879-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34879-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="34879-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34879-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34879-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34879-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34879-124">Remarks</span></span>  
 <span data-ttu-id="34879-125">`IHostSecurityManager::SetThreadToken` zachowuje się podobnie do odpowiednich funkcji Win32 o takiej samej nazwie, z tą różnicą, że funkcja Win32 pozwala na obiekt wywołujący, aby przekazać dojścia do dowolnego wątku, podczas gdy `IHostSecurityManager::SetThreadToken` tylko z aktualnie wykonywany Wątek można skojarzyć token.</span><span class="sxs-lookup"><span data-stu-id="34879-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="34879-126">`HANDLE` Typ nie jest zgodny z COM; oznacza to, jego rozmiar jest specyficzne dla systemu operacyjnego i potrzebny organizowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="34879-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="34879-127">W związku z tym ten token jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.</span><span class="sxs-lookup"><span data-stu-id="34879-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34879-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34879-128">Requirements</span></span>  
 <span data-ttu-id="34879-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34879-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34879-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34879-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34879-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34879-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34879-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34879-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34879-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34879-133">See also</span></span>

- [<span data-ttu-id="34879-134">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="34879-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="34879-135">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="34879-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
