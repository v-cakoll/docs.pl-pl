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
ms.openlocfilehash: a7dae98d1f2dc2448bd3a5df2d6143b7be0bb734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129258"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="cc6b2-102">ICLRGCManager::Collect — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc6b2-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="cc6b2-103">Wymusza wyrzucanie elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc6b2-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc6b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc6b2-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="cc6b2-106">podczas Generacja do zebrania.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-106">[in] The generation to collect.</span></span> <span data-ttu-id="cc6b2-107">Wartość-1 wymusza zbieranie wszystkich generacji.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc6b2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cc6b2-108">Return Value</span></span>  
  
|<span data-ttu-id="cc6b2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc6b2-109">HRESULT</span></span>|<span data-ttu-id="cc6b2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cc6b2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc6b2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc6b2-111">S_OK</span></span>|<span data-ttu-id="cc6b2-112">`Collect` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="cc6b2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc6b2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc6b2-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc6b2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc6b2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc6b2-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-116">The call timed out.</span></span>|  
|<span data-ttu-id="cc6b2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc6b2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc6b2-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc6b2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc6b2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc6b2-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc6b2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc6b2-121">E_FAIL</span></span>|<span data-ttu-id="cc6b2-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc6b2-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc6b2-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc6b2-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc6b2-125">Remarks</span></span>  
 <span data-ttu-id="cc6b2-126">Metoda `Collect` wymusza Moduł wyrzucania elementów bezużytecznych środowiska CLR w celu przeprowadzenia kolekcji niezależnie od jej bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="cc6b2-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc6b2-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc6b2-127">Requirements</span></span>  
 <span data-ttu-id="cc6b2-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc6b2-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc6b2-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc6b2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc6b2-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc6b2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc6b2-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc6b2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6b2-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc6b2-132">See also</span></span>

- [<span data-ttu-id="cc6b2-133">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="cc6b2-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="cc6b2-134">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="cc6b2-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="cc6b2-135">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc6b2-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="cc6b2-136">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc6b2-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="cc6b2-137">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="cc6b2-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="cc6b2-138">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cc6b2-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="cc6b2-139">Hosting</span><span class="sxs-lookup"><span data-stu-id="cc6b2-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
