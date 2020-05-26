---
title: IHostMemoryManager::VirtualQuery — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
ms.openlocfilehash: 71c56b5dab2409be05e8260b1a2e39d28a709bba
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804366"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="0bc45-102">IHostMemoryManager::VirtualQuery — Metoda</span><span class="sxs-lookup"><span data-stu-id="0bc45-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="0bc45-103">Służy jako otoka logiczna dla odpowiadającej jej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="0bc45-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="0bc45-104">Implementacja Win32 `VirtualQuery` Pobiera informacje o zakresie stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0bc45-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc45-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bc45-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bc45-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bc45-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="0bc45-107">podczas Wskaźnik na adres w pamięci wirtualnej, który ma być wysyłany do zapytania.</span><span class="sxs-lookup"><span data-stu-id="0bc45-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="0bc45-108">określoną Wskaźnik do struktury zawierającej informacje o określonym regionie pamięci.</span><span class="sxs-lookup"><span data-stu-id="0bc45-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="0bc45-109">podczas Rozmiar (w bajtach) bufora, który `lpBuffer` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="0bc45-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="0bc45-110">określoną Wskaźnik do liczby bajtów zwróconych przez bufor informacji.</span><span class="sxs-lookup"><span data-stu-id="0bc45-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bc45-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0bc45-111">Return Value</span></span>  
  
|<span data-ttu-id="0bc45-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0bc45-112">HRESULT</span></span>|<span data-ttu-id="0bc45-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0bc45-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bc45-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0bc45-114">S_OK</span></span>|<span data-ttu-id="0bc45-115">`VirtualQuery`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="0bc45-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="0bc45-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0bc45-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0bc45-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0bc45-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0bc45-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0bc45-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0bc45-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="0bc45-119">The call timed out.</span></span>|  
|<span data-ttu-id="0bc45-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0bc45-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0bc45-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0bc45-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0bc45-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0bc45-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0bc45-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="0bc45-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0bc45-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0bc45-124">E_FAIL</span></span>|<span data-ttu-id="0bc45-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0bc45-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0bc45-126">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="0bc45-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0bc45-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0bc45-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bc45-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0bc45-128">Remarks</span></span>  
 <span data-ttu-id="0bc45-129">`VirtualQuery`zawiera informacje o zakresie stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0bc45-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="0bc45-130">Ta implementacja ustawia wartość `pResult` parametru na liczbę bajtów zwracanych w buforze informacji i zwraca wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0bc45-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="0bc45-131">W funkcji Win32 `VirtualQuery` wartość zwracana jest rozmiarem buforu.</span><span class="sxs-lookup"><span data-stu-id="0bc45-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="0bc45-132">Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0bc45-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0bc45-133">Implementacja systemu operacyjnego nie pociągnie za `VirtualQuery` sobą zakleszczenie i może działać do ukończenia z losowymi wątkami zawieszonymi w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0bc45-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="0bc45-134">Należy zachować ostrożność podczas implementowania hostowanej wersji tej metody.</span><span class="sxs-lookup"><span data-stu-id="0bc45-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bc45-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0bc45-135">Requirements</span></span>  
 <span data-ttu-id="0bc45-136">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bc45-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bc45-137">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0bc45-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0bc45-138">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0bc45-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0bc45-139">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bc45-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc45-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bc45-140">See also</span></span>

- [<span data-ttu-id="0bc45-141">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0bc45-141">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
