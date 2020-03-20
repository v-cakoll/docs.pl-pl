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
ms.openlocfilehash: 88acd50c83eb1ff4d59aa50d677db2383912659a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176282"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="e190c-102">IHostMemoryManager::GetMemoryLoad — Metoda</span><span class="sxs-lookup"><span data-stu-id="e190c-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="e190c-103">Pobiera ilość pamięci fizycznej, która jest obecnie w użyciu i dlatego niedostępne, zgodnie z raportem przez hosta.</span><span class="sxs-lookup"><span data-stu-id="e190c-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e190c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e190c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e190c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e190c-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="e190c-106">[na zewnątrz] Wskaźnik do przybliżonego procentu całkowitej pamięci fizycznej, która jest aktualnie używana.</span><span class="sxs-lookup"><span data-stu-id="e190c-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="e190c-107">[na zewnątrz] Wskaźnik do liczby bajtów dostępnych dla środowiska wykonawczego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e190c-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e190c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e190c-108">Return Value</span></span>  
  
|<span data-ttu-id="e190c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e190c-109">HRESULT</span></span>|<span data-ttu-id="e190c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="e190c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e190c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e190c-111">S_OK</span></span>|<span data-ttu-id="e190c-112">`GetMemoryLoad`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e190c-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="e190c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e190c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e190c-114">Clr nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e190c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e190c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e190c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e190c-116">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e190c-116">The call timed out.</span></span>|  
|<span data-ttu-id="e190c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e190c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e190c-118">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e190c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e190c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e190c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e190c-120">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="e190c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e190c-121">E_fail</span><span class="sxs-lookup"><span data-stu-id="e190c-121">E_FAIL</span></span>|<span data-ttu-id="e190c-122">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="e190c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e190c-123">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e190c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e190c-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e190c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e190c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e190c-125">Remarks</span></span>  
 <span data-ttu-id="e190c-126">`GetMemoryLoad`zawija funkcję `GlobalMemoryStatus` Win32.</span><span class="sxs-lookup"><span data-stu-id="e190c-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="e190c-127">Wartość jest `pMemoryLoad` odpowiednikiem `dwMemoryLoad` pola w `MEMORYSTATUS` strukturze zwróconej z `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="e190c-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="e190c-128">Środowisko wykonawcze używa zwracanej wartości jako heurystyki dla modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="e190c-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="e190c-129">Na przykład jeśli host zgłasza, że większość pamięci jest w użyciu, moduł zbierający elementy bezużyteczne może wybrać do zbierania z wielu pokoleń, aby zwiększyć ilość pamięci, które mogą potencjalnie stać się dostępne.</span><span class="sxs-lookup"><span data-stu-id="e190c-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e190c-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e190c-130">Requirements</span></span>  
 <span data-ttu-id="e190c-131">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e190c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e190c-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e190c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e190c-133">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e190c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e190c-134">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e190c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e190c-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e190c-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="e190c-136">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e190c-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
