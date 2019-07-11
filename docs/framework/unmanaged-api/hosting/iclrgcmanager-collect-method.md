---
title: ICLRGCManager::Collect — Metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4b05ab56a6837899a6047da17affe1810ad8292
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772795"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="1d748-102">ICLRGCManager::Collect — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d748-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="1d748-103">Wymusza wyrzucania elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="1d748-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d748-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d748-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d748-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d748-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="1d748-106">[in] Generowanie do zbierania.</span><span class="sxs-lookup"><span data-stu-id="1d748-106">[in] The generation to collect.</span></span> <span data-ttu-id="1d748-107">Wartość -1 powoduje zbiór wszystkich generacji.</span><span class="sxs-lookup"><span data-stu-id="1d748-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d748-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1d748-108">Return Value</span></span>  
  
|<span data-ttu-id="1d748-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d748-109">HRESULT</span></span>|<span data-ttu-id="1d748-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1d748-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d748-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d748-111">S_OK</span></span>|<span data-ttu-id="1d748-112">`Collect` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="1d748-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="1d748-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d748-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d748-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1d748-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d748-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d748-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d748-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1d748-116">The call timed out.</span></span>|  
|<span data-ttu-id="1d748-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d748-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d748-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="1d748-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d748-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d748-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d748-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1d748-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d748-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d748-121">E_FAIL</span></span>|<span data-ttu-id="1d748-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1d748-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d748-123">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1d748-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d748-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1d748-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d748-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d748-125">Remarks</span></span>  
 <span data-ttu-id="1d748-126">`Collect` Metoda wymusza moduł odśmiecania pamięci CLR na wykonywanie odśmiecania niezależnie od tego, w jego bieżącym stanie.</span><span class="sxs-lookup"><span data-stu-id="1d748-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d748-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d748-127">Requirements</span></span>  
 <span data-ttu-id="1d748-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d748-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d748-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d748-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d748-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1d748-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d748-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d748-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d748-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d748-132">See also</span></span>

- [<span data-ttu-id="1d748-133">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="1d748-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="1d748-134">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="1d748-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="1d748-135">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d748-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="1d748-136">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d748-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="1d748-137">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="1d748-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="1d748-138">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1d748-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1d748-139">Hosting</span><span class="sxs-lookup"><span data-stu-id="1d748-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
