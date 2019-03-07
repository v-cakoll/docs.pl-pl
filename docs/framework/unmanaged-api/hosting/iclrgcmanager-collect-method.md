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
ms.openlocfilehash: 2da0b3b7a8a7ae46050345aaf5fcfa65fa349ae5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477988"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="fbf0c-102">ICLRGCManager::Collect — Metoda</span><span class="sxs-lookup"><span data-stu-id="fbf0c-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="fbf0c-103">Wymusza wyrzucania elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf0c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbf0c-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbf0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbf0c-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="fbf0c-106">[in] Generowanie do zbierania.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-106">[in] The generation to collect.</span></span> <span data-ttu-id="fbf0c-107">Wartość -1 powoduje zbiór wszystkich generacji.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbf0c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fbf0c-108">Return Value</span></span>  
  
|<span data-ttu-id="fbf0c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbf0c-109">HRESULT</span></span>|<span data-ttu-id="fbf0c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fbf0c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbf0c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbf0c-111">S_OK</span></span>|<span data-ttu-id="fbf0c-112">`Collect` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="fbf0c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fbf0c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fbf0c-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fbf0c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fbf0c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fbf0c-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-116">The call timed out.</span></span>|  
|<span data-ttu-id="fbf0c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fbf0c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fbf0c-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fbf0c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fbf0c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fbf0c-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fbf0c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fbf0c-121">E_FAIL</span></span>|<span data-ttu-id="fbf0c-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fbf0c-123">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fbf0c-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbf0c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fbf0c-125">Remarks</span></span>  
 <span data-ttu-id="fbf0c-126">`Collect` Metoda wymusza moduł odśmiecania pamięci CLR na wykonywanie odśmiecania niezależnie od tego, w jego bieżącym stanie.</span><span class="sxs-lookup"><span data-stu-id="fbf0c-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbf0c-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fbf0c-127">Requirements</span></span>  
 <span data-ttu-id="fbf0c-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbf0c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbf0c-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbf0c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbf0c-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbf0c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbf0c-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbf0c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf0c-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbf0c-132">See also</span></span>
- [<span data-ttu-id="fbf0c-133">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="fbf0c-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="fbf0c-134">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="fbf0c-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="fbf0c-135">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbf0c-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="fbf0c-136">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbf0c-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="fbf0c-137">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="fbf0c-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="fbf0c-138">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fbf0c-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="fbf0c-139">Hosting</span><span class="sxs-lookup"><span data-stu-id="fbf0c-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
