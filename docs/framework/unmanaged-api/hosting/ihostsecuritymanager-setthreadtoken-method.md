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
ms.openlocfilehash: 7891ddc5085eedd2a9010023f119d08f101e2fa3
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803776"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="228fb-102">IHostSecurityManager::SetThreadToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="228fb-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="228fb-103">Ustawia dojście dla aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="228fb-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="228fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="228fb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="228fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="228fb-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="228fb-106">podczas Uchwyt do tokenu, który ma zostać ustawiony dla aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="228fb-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="228fb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="228fb-107">Return Value</span></span>  
  
|<span data-ttu-id="228fb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="228fb-108">HRESULT</span></span>|<span data-ttu-id="228fb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="228fb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="228fb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="228fb-110">S_OK</span></span>|<span data-ttu-id="228fb-111">`SetThreadToken`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="228fb-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="228fb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="228fb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="228fb-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="228fb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="228fb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="228fb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="228fb-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="228fb-115">The call timed out.</span></span>|  
|<span data-ttu-id="228fb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="228fb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="228fb-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="228fb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="228fb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="228fb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="228fb-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="228fb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="228fb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="228fb-120">E_FAIL</span></span>|<span data-ttu-id="228fb-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="228fb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="228fb-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="228fb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="228fb-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="228fb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="228fb-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="228fb-124">Remarks</span></span>  
 <span data-ttu-id="228fb-125">`IHostSecurityManager::SetThreadToken`zachowuje się podobnie do odpowiedniej funkcji Win32 o tej samej nazwie, z tą różnicą, że funkcja Win32 zezwala obiektowi wywołującemu na przekazywanie dojścia do dowolnego wątku, podczas gdy `IHostSecurityManager::SetThreadToken` może skojarzyć token tylko z aktualnie wykonywanym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="228fb-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="228fb-126">`HANDLE`Typ nie jest zgodny z modelem com; oznacza to, że jego rozmiar jest specyficzny dla systemu operacyjnego i wymaga kierowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="228fb-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="228fb-127">W ten sposób token jest używany tylko w ramach procesu, między środowiskiem CLR a hostem.</span><span class="sxs-lookup"><span data-stu-id="228fb-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="228fb-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="228fb-128">Requirements</span></span>  
 <span data-ttu-id="228fb-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="228fb-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="228fb-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="228fb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="228fb-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="228fb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="228fb-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="228fb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228fb-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="228fb-133">See also</span></span>

- [<span data-ttu-id="228fb-134">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="228fb-134">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="228fb-135">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="228fb-135">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
