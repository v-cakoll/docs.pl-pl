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
ms.openlocfilehash: 1dd5ed4c556a5a4d4425a9c0730cebf22ff1785b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804620"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="c5411-102">IHostMAlloc::Free — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5411-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="c5411-103">Zwalnia pamięć przydzieloną przy użyciu funkcji [Alloc](ihostmalloc-alloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c5411-103">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5411-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5411-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5411-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5411-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="c5411-106">podczas Wskaźnik do pamięci, która ma zostać zwolniona.</span><span class="sxs-lookup"><span data-stu-id="c5411-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5411-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c5411-107">Return Value</span></span>  
  
|<span data-ttu-id="c5411-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5411-108">HRESULT</span></span>|<span data-ttu-id="c5411-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c5411-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5411-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5411-110">S_OK</span></span>|<span data-ttu-id="c5411-111">`Free`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="c5411-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="c5411-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5411-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5411-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c5411-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5411-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5411-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5411-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="c5411-115">The call timed out.</span></span>|  
|<span data-ttu-id="c5411-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5411-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5411-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="c5411-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5411-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5411-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5411-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="c5411-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5411-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5411-120">E_FAIL</span></span>|<span data-ttu-id="c5411-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c5411-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5411-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="c5411-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5411-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c5411-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c5411-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="c5411-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="c5411-125">Podjęto próbę zwolnienia pamięci, która nie została przyalokowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="c5411-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5411-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5411-126">Remarks</span></span>  
 <span data-ttu-id="c5411-127">Jeśli `pMem` parametr odnosi się do regionu pamięci, który nie został przydzielony przy użyciu wywołania do `Alloc` , host powinien zwrócić HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="c5411-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5411-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5411-128">Requirements</span></span>  
 <span data-ttu-id="c5411-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5411-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5411-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c5411-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5411-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c5411-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5411-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5411-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5411-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5411-133">See also</span></span>

- [<span data-ttu-id="c5411-134">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5411-134">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="c5411-135">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5411-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
