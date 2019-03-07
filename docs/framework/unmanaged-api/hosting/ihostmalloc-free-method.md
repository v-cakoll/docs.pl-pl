---
title: IHostMAlloc::Free — Metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cf60d4e711d0c88b5fb8b4c213b19bdea564324
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477832"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="6b10f-102">IHostMAlloc::Free — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b10f-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="6b10f-103">Zwalnia pamięć, która została przydzielona za pomocą [alokacji](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="6b10f-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b10f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b10f-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b10f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b10f-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="6b10f-106">[in] Wskaźnik do pamięci, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="6b10f-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b10f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b10f-107">Return Value</span></span>  
  
|<span data-ttu-id="6b10f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b10f-108">HRESULT</span></span>|<span data-ttu-id="6b10f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6b10f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b10f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b10f-110">S_OK</span></span>|<span data-ttu-id="6b10f-111">`Free` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="6b10f-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="6b10f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b10f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b10f-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b10f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b10f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b10f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b10f-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b10f-115">The call timed out.</span></span>|  
|<span data-ttu-id="6b10f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b10f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b10f-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="6b10f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b10f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b10f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b10f-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6b10f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b10f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b10f-120">E_FAIL</span></span>|<span data-ttu-id="6b10f-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6b10f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b10f-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6b10f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b10f-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b10f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6b10f-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="6b10f-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="6b10f-125">Nastąpiła próba, aby zwolnić pamięć, która nie została przydzielona za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="6b10f-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b10f-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b10f-126">Remarks</span></span>  
 <span data-ttu-id="6b10f-127">Jeśli `pMem` parametr odnosi się do regionu pamięci, która nie została przydzielona za pomocą wywołania `Alloc`, host powinien zwrócić HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="6b10f-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b10f-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b10f-128">Requirements</span></span>  
 <span data-ttu-id="6b10f-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b10f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b10f-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b10f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b10f-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b10f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b10f-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b10f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b10f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b10f-133">See also</span></span>
- [<span data-ttu-id="6b10f-134">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b10f-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="6b10f-135">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b10f-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
