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
ms.openlocfilehash: 21342af13f9d77ebab979102172e1a2c28402273
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108059"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="140a9-102">IHostMAlloc::Free — Metoda</span><span class="sxs-lookup"><span data-stu-id="140a9-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="140a9-103">Zwalnia pamięć, która została przydzielona za pomocą [alokacji](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="140a9-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="140a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="140a9-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="140a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="140a9-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="140a9-106">[in] Wskaźnik do pamięci, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="140a9-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="140a9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="140a9-107">Return Value</span></span>  
  
|<span data-ttu-id="140a9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="140a9-108">HRESULT</span></span>|<span data-ttu-id="140a9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="140a9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="140a9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="140a9-110">S_OK</span></span>|`Free` <span data-ttu-id="140a9-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="140a9-111">returned successfully.</span></span>|  
|<span data-ttu-id="140a9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="140a9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="140a9-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="140a9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="140a9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="140a9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="140a9-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="140a9-115">The call timed out.</span></span>|  
|<span data-ttu-id="140a9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="140a9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="140a9-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="140a9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="140a9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="140a9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="140a9-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="140a9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="140a9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="140a9-120">E_FAIL</span></span>|<span data-ttu-id="140a9-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="140a9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="140a9-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="140a9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="140a9-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="140a9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="140a9-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="140a9-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="140a9-125">Nastąpiła próba, aby zwolnić pamięć, która nie została przydzielona za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="140a9-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="140a9-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="140a9-126">Remarks</span></span>  
 <span data-ttu-id="140a9-127">Jeśli `pMem` parametr odnosi się do regionu pamięci, która nie została przydzielona za pomocą wywołania `Alloc`, host powinien zwrócić HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="140a9-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="140a9-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="140a9-128">Requirements</span></span>  
 <span data-ttu-id="140a9-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="140a9-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="140a9-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="140a9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="140a9-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="140a9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="140a9-132">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="140a9-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="140a9-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="140a9-133">See also</span></span>

- [<span data-ttu-id="140a9-134">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="140a9-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="140a9-135">IHostMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="140a9-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
