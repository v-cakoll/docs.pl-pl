---
title: IHostMAlloc::DebugAlloc — Metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 8475362ede5ea28009d5abc54c286d6f2a6fed0f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804634"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="e31f6-102">IHostMAlloc::DebugAlloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="e31f6-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="e31f6-103">Żąda, aby Host przydzielił określoną ilość pamięci ze sterty, a także śledzić miejsce przydzielenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="e31f6-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e31f6-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e31f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e31f6-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="e31f6-106">podczas Rozmiar (w bajtach) bieżącego żądania alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="e31f6-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="e31f6-107">podczas Jedna z wartości [EMemoryCriticalLevel —](ememorycriticallevel-enumeration.md) , co wskazuje na wpływ błędu alokacji.</span><span class="sxs-lookup"><span data-stu-id="e31f6-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="e31f6-108">podczas Plik kodu debugowanego pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="e31f6-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="e31f6-109">podczas Numer wiersza, w `pszFileName` którym zażądano alokacji.</span><span class="sxs-lookup"><span data-stu-id="e31f6-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="e31f6-110">określoną Wskaźnik do przydzieloną pamięci lub wartość null, jeśli nie można ukończyć żądania.</span><span class="sxs-lookup"><span data-stu-id="e31f6-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e31f6-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e31f6-111">Return Value</span></span>  
  
|<span data-ttu-id="e31f6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e31f6-112">HRESULT</span></span>|<span data-ttu-id="e31f6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e31f6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e31f6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e31f6-114">S_OK</span></span>|<span data-ttu-id="e31f6-115">`DebugAlloc`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="e31f6-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="e31f6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e31f6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e31f6-117">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e31f6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e31f6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e31f6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e31f6-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e31f6-119">The call timed out.</span></span>|  
|<span data-ttu-id="e31f6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e31f6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e31f6-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e31f6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e31f6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e31f6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e31f6-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="e31f6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e31f6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e31f6-124">E_FAIL</span></span>|<span data-ttu-id="e31f6-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e31f6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e31f6-126">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="e31f6-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e31f6-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e31f6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e31f6-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e31f6-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e31f6-129">Za mało dostępnej pamięci, aby ukończyć żądanie alokacji.</span><span class="sxs-lookup"><span data-stu-id="e31f6-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e31f6-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e31f6-130">Remarks</span></span>  
 <span data-ttu-id="e31f6-131">Środowisko CLR Pobiera wskaźnik interfejsu do wystąpienia [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) przez wywołanie metody [IHostMemoryManager::](ihostmemorymanager-createmalloc-method.md) CreateInstance.</span><span class="sxs-lookup"><span data-stu-id="e31f6-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="e31f6-132">`DebugAlloc`umożliwia środowisko uruchomieniowe pobieranie informacji o pliku kodu do użycia podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="e31f6-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e31f6-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e31f6-133">Requirements</span></span>  
 <span data-ttu-id="e31f6-134">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e31f6-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e31f6-135">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e31f6-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e31f6-136">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e31f6-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e31f6-137">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e31f6-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e31f6-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e31f6-138">See also</span></span>

- [<span data-ttu-id="e31f6-139">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e31f6-139">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="e31f6-140">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="e31f6-140">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
