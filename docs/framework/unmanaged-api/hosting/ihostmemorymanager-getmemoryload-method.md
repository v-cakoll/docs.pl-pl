---
title: IHostMemoryManager::GetMemoryLoad — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53001d6dfef2813df86dc4bb4f9647900143aae7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469069"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="a7113-102">IHostMemoryManager::GetMemoryLoad — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7113-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="a7113-103">Pobiera ilość pamięci fizycznej, która jest obecnie w użyciu i w związku z tym niedostępny jako zgłaszane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="a7113-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7113-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7113-104">Syntax</span></span>  
  
```  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7113-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7113-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="a7113-106">[out] Wskaźnik do przybliżony procent całkowitej pamięci fizycznej, która jest obecnie w użyciu.</span><span class="sxs-lookup"><span data-stu-id="a7113-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="a7113-107">[out] Wskaźnik do liczby bajtów dostępnych do środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a7113-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7113-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7113-108">Return Value</span></span>  
  
|<span data-ttu-id="a7113-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7113-109">HRESULT</span></span>|<span data-ttu-id="a7113-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a7113-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7113-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7113-111">S_OK</span></span>|<span data-ttu-id="a7113-112">`GetMemoryLoad` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a7113-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="a7113-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7113-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7113-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a7113-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7113-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7113-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7113-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a7113-116">The call timed out.</span></span>|  
|<span data-ttu-id="a7113-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7113-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7113-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a7113-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7113-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7113-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7113-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a7113-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7113-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7113-121">E_FAIL</span></span>|<span data-ttu-id="a7113-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a7113-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7113-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a7113-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7113-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a7113-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7113-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7113-125">Remarks</span></span>  
 <span data-ttu-id="a7113-126">`GetMemoryLoad` opakowuje Win32 `GlobalMemoryStatus` funkcji.</span><span class="sxs-lookup"><span data-stu-id="a7113-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="a7113-127">Wartość `pMemoryLoad` jest odpowiednikiem `dwMemoryLoad` pole `MEMORYSTATUS` struktury zwróciło `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="a7113-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="a7113-128">Środowisko wykonawcze używa wartość zwracaną jako heurystykę dla modułu odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="a7113-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="a7113-129">Na przykład jeśli host zgłasza, że większość pamięci jest w użyciu, wyrzucanie elementów bezużytecznych może zdecydować się na zbieranie z wielu generacji, aby zwiększyć ilość pamięci, która może być potencjalnie staną się dostępne.</span><span class="sxs-lookup"><span data-stu-id="a7113-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7113-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7113-130">Requirements</span></span>  
 <span data-ttu-id="a7113-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7113-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7113-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7113-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7113-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7113-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7113-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7113-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7113-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7113-135">See also</span></span>
- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="a7113-136">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7113-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
