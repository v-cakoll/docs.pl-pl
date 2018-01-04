---
title: "IHostMAlloc::Free — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Free
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4775b6ae00f34d7d046515f8700a35470b2f6650
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="fa7e3-102">IHostMAlloc::Free — Metoda</span><span class="sxs-lookup"><span data-stu-id="fa7e3-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="fa7e3-103">Zwalnia pamięć, która została przydzielona przy użyciu [alokacji](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa7e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa7e3-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa7e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa7e3-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="fa7e3-106">[in] Wskaźnik do pamięci, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa7e3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fa7e3-107">Return Value</span></span>  
  
|<span data-ttu-id="fa7e3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa7e3-108">HRESULT</span></span>|<span data-ttu-id="fa7e3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fa7e3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa7e3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa7e3-110">S_OK</span></span>|<span data-ttu-id="fa7e3-111">`Free`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="fa7e3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fa7e3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fa7e3-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fa7e3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fa7e3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fa7e3-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-115">The call timed out.</span></span>|  
|<span data-ttu-id="fa7e3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fa7e3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fa7e3-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fa7e3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fa7e3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fa7e3-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fa7e3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa7e3-120">E_FAIL</span></span>|<span data-ttu-id="fa7e3-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fa7e3-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fa7e3-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fa7e3-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="fa7e3-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="fa7e3-125">Nastąpiła próba zwolnienia pamięci, która nie została przydzielona za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa7e3-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa7e3-126">Remarks</span></span>  
 <span data-ttu-id="fa7e3-127">Jeśli `pMem` parametr odnosi się do obszaru pamięci, który nie został przydzielony przy użyciu wywołania `Alloc`, hosta powinien zwrócić HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="fa7e3-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa7e3-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa7e3-128">Requirements</span></span>  
 <span data-ttu-id="fa7e3-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa7e3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa7e3-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fa7e3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa7e3-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fa7e3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa7e3-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa7e3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7e3-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa7e3-133">See Also</span></span>  
 [<span data-ttu-id="fa7e3-134">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7e3-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="fa7e3-135">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7e3-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
