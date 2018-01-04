---
title: "IHostSecurityManager::SetThreadToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.SetThreadToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35418907c2b3c75fef689e53b9d6b86ded1f2570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="da837-102">IHostSecurityManager::SetThreadToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="da837-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="da837-103">Ustawia dojście wątku aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="da837-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da837-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da837-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da837-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da837-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="da837-106">[in] Dojście do tokenu można ustawić dla wątku aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="da837-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da837-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="da837-107">Return Value</span></span>  
  
|<span data-ttu-id="da837-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da837-108">HRESULT</span></span>|<span data-ttu-id="da837-109">Opis</span><span class="sxs-lookup"><span data-stu-id="da837-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da837-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="da837-110">S_OK</span></span>|<span data-ttu-id="da837-111">`SetThreadToken`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="da837-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="da837-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da837-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da837-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="da837-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da837-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da837-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da837-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="da837-115">The call timed out.</span></span>|  
|<span data-ttu-id="da837-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da837-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da837-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="da837-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da837-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da837-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da837-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="da837-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da837-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da837-120">E_FAIL</span></span>|<span data-ttu-id="da837-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="da837-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da837-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="da837-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da837-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="da837-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da837-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da837-124">Remarks</span></span>  
 <span data-ttu-id="da837-125">`IHostSecurityManager::SetThreadToken`działa podobnie do funkcji Win32 odpowiedniego o takiej samej nazwie, z tą różnicą, że funkcja Win32 umożliwia obiekt wywołujący, aby przekazać w dojścia do dowolnego wątku, podczas `IHostSecurityManager::SetThreadToken` można skojarzyć token tylko z wątku aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="da837-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="da837-126">`HANDLE` Typ nie jest zgodny z interfejsem COM; to, że jego rozmiar jest specyficzna dla systemu operacyjnego i wymaga przekazywanie niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="da837-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="da837-127">W związku z tym token ten jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.</span><span class="sxs-lookup"><span data-stu-id="da837-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da837-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da837-128">Requirements</span></span>  
 <span data-ttu-id="da837-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da837-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da837-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="da837-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da837-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da837-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da837-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da837-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da837-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da837-133">See Also</span></span>  
 [<span data-ttu-id="da837-134">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="da837-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="da837-135">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="da837-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
