---
title: "ICLRGCManager::Collect — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.Collect
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96f99855654a3a86873ca4623d8617f74030938b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="3a089-102">ICLRGCManager::Collect — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a089-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="3a089-103">Wymusza wyrzucania elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="3a089-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a089-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a089-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a089-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a089-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="3a089-106">[in] Generowanie do zbierania.</span><span class="sxs-lookup"><span data-stu-id="3a089-106">[in] The generation to collect.</span></span> <span data-ttu-id="3a089-107">Wartość -1 powoduje to zbiór wszystkich generacji.</span><span class="sxs-lookup"><span data-stu-id="3a089-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a089-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3a089-108">Return Value</span></span>  
  
|<span data-ttu-id="3a089-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a089-109">HRESULT</span></span>|<span data-ttu-id="3a089-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3a089-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a089-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a089-111">S_OK</span></span>|<span data-ttu-id="3a089-112">`Collect`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3a089-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="3a089-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a089-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a089-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="3a089-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a089-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a089-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a089-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="3a089-116">The call timed out.</span></span>|  
|<span data-ttu-id="3a089-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a089-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a089-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="3a089-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a089-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a089-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a089-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="3a089-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a089-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a089-121">E_FAIL</span></span>|<span data-ttu-id="3a089-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3a089-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a089-123">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="3a089-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a089-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3a089-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a089-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a089-125">Remarks</span></span>  
 <span data-ttu-id="3a089-126">`Collect` Metody wymusza moduł Garbage Collector środowiska CLR do wykonania kolekcji niezależnie od bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="3a089-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a089-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a089-127">Requirements</span></span>  
 <span data-ttu-id="3a089-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a089-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a089-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a089-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a089-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a089-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a089-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a089-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a089-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a089-132">See Also</span></span>  
 [<span data-ttu-id="3a089-133">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="3a089-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="3a089-134">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="3a089-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="3a089-135">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="3a089-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3a089-136">ICLRGCManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="3a089-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="3a089-137">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="3a089-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="3a089-138">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="3a089-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="3a089-139">Hosting</span><span class="sxs-lookup"><span data-stu-id="3a089-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
