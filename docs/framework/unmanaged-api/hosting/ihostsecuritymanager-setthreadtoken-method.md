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
ms.openlocfilehash: aa17f637ef71373697db5ce66e4a6540c5cc5fbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139495"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="fa882-102">IHostSecurityManager::SetThreadToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="fa882-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="fa882-103">Ustawia dojście dla aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="fa882-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa882-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa882-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa882-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa882-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="fa882-106">podczas Uchwyt do tokenu, który ma zostać ustawiony dla aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="fa882-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa882-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fa882-107">Return Value</span></span>  
  
|<span data-ttu-id="fa882-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa882-108">HRESULT</span></span>|<span data-ttu-id="fa882-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fa882-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa882-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa882-110">S_OK</span></span>|<span data-ttu-id="fa882-111">`SetThreadToken` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="fa882-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="fa882-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fa882-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fa882-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fa882-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fa882-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fa882-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fa882-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="fa882-115">The call timed out.</span></span>|  
|<span data-ttu-id="fa882-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fa882-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fa882-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="fa882-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fa882-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fa882-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fa882-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="fa882-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fa882-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa882-120">E_FAIL</span></span>|<span data-ttu-id="fa882-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fa882-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fa882-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="fa882-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fa882-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fa882-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa882-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa882-124">Remarks</span></span>  
 <span data-ttu-id="fa882-125">`IHostSecurityManager::SetThreadToken` zachowuje się podobnie do odpowiedniej funkcji Win32 o tej samej nazwie, z tą różnicą, że funkcja Win32 zezwala obiektowi wywołującemu na przekazywanie dojścia do dowolnego wątku, podczas gdy `IHostSecurityManager::SetThreadToken` może skojarzyć token tylko z aktualnie wykonywanym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="fa882-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="fa882-126">Typ `HANDLE` nie jest zgodny z modelem COM; oznacza to, że jego rozmiar jest specyficzny dla systemu operacyjnego i wymaga organizowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="fa882-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="fa882-127">W ten sposób token jest używany tylko w ramach procesu, między środowiskiem CLR a hostem.</span><span class="sxs-lookup"><span data-stu-id="fa882-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa882-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa882-128">Requirements</span></span>  
 <span data-ttu-id="fa882-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa882-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa882-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fa882-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa882-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fa882-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa882-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa882-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa882-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa882-133">See also</span></span>

- [<span data-ttu-id="fa882-134">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa882-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="fa882-135">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa882-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
