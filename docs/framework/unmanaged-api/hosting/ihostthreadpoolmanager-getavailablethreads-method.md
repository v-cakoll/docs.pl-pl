---
title: IHostThreadPoolManager::GetAvailableThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
ms.openlocfilehash: cc03960c2d45a6cf8aed58eaf048a0531decb08f
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842338"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="b8882-102">IHostThreadPoolManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="b8882-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="b8882-103">Pobiera liczbę wątków w puli wątków, które nie przetwarzają obecnie elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="b8882-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8882-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8882-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8882-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8882-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="b8882-106">określoną Wskaźnik do liczby wątków w puli wątków, które nie przetwarzają obecnie elementów roboczych.</span><span class="sxs-lookup"><span data-stu-id="b8882-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8882-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b8882-107">Return Value</span></span>  
  
|<span data-ttu-id="b8882-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8882-108">HRESULT</span></span>|<span data-ttu-id="b8882-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b8882-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8882-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8882-110">S_OK</span></span>|<span data-ttu-id="b8882-111">`GetAvailableThreads`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="b8882-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b8882-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b8882-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b8882-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b8882-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b8882-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b8882-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b8882-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b8882-115">The call timed out.</span></span>|  
|<span data-ttu-id="b8882-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b8882-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b8882-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b8882-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b8882-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b8882-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b8882-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="b8882-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b8882-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b8882-120">E_FAIL</span></span>|<span data-ttu-id="b8882-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b8882-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b8882-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="b8882-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b8882-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b8882-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b8882-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b8882-124">E_NOTIMPL</span></span>|<span data-ttu-id="b8882-125">Host nie oferuje implementacji programu `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="b8882-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8882-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8882-126">Remarks</span></span>  
 <span data-ttu-id="b8882-127">Jeśli host nie dostarcza implementacji `GetAvailableThreads` , powinien zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b8882-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8882-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8882-128">Requirements</span></span>  
 <span data-ttu-id="b8882-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8882-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8882-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b8882-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8882-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b8882-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8882-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8882-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8882-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8882-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="b8882-134">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8882-134">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
