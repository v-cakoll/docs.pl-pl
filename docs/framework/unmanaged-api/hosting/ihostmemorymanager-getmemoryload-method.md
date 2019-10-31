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
ms.openlocfilehash: 2210dcd9e8a8af92b7905ec680c53c1119e6a3cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136706"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="f9995-102">IHostMemoryManager::GetMemoryLoad — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9995-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="f9995-103">Pobiera ilość pamięci fizycznej, która jest aktualnie używana, i dlatego jest niedostępna, zgodnie z informacjami o hoście.</span><span class="sxs-lookup"><span data-stu-id="f9995-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9995-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9995-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9995-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9995-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="f9995-106">określoną Wskaźnik do przybliżonej wartości procentowej całkowitej ilości pamięci fizycznej, która jest obecnie używana.</span><span class="sxs-lookup"><span data-stu-id="f9995-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="f9995-107">określoną Wskaźnik do liczby bajtów dostępnych dla środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f9995-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9995-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f9995-108">Return Value</span></span>  
  
|<span data-ttu-id="f9995-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9995-109">HRESULT</span></span>|<span data-ttu-id="f9995-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f9995-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9995-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9995-111">S_OK</span></span>|<span data-ttu-id="f9995-112">`GetMemoryLoad` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="f9995-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="f9995-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9995-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9995-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9995-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9995-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9995-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9995-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f9995-116">The call timed out.</span></span>|  
|<span data-ttu-id="f9995-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9995-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9995-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f9995-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9995-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9995-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9995-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="f9995-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9995-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9995-121">E_FAIL</span></span>|<span data-ttu-id="f9995-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f9995-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9995-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="f9995-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9995-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f9995-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9995-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9995-125">Remarks</span></span>  
 <span data-ttu-id="f9995-126">`GetMemoryLoad` zawija funkcję Win32 `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="f9995-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="f9995-127">Wartość `pMemoryLoad` jest odpowiednikiem pola `dwMemoryLoad` w strukturze `MEMORYSTATUS` zwróconej z `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="f9995-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="f9995-128">Środowisko uruchomieniowe używa wartości zwracanej jako algorytmu heurystycznego modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f9995-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="f9995-129">Na przykład jeśli Host zgłasza, że większość pamięci jest w użyciu, Moduł wyrzucania elementów bezużytecznych może wybrać zbieranie z wielu generacji w celu zwiększenia ilości pamięci, która może być dostępna.</span><span class="sxs-lookup"><span data-stu-id="f9995-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9995-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9995-130">Requirements</span></span>  
 <span data-ttu-id="f9995-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9995-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9995-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9995-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9995-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f9995-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9995-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9995-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9995-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9995-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="f9995-136">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f9995-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
