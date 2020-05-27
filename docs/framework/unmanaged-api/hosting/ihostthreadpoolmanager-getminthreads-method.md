---
title: IHostThreadPoolManager::GetMinThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
ms.openlocfilehash: a05cfb43b5b4a328d22c4df04049a7fa156ca080
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841935"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="22a1d-102">IHostThreadPoolManager::GetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="22a1d-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="22a1d-103">Pobiera minimalną liczbę bezczynnych wątków, które Host przechowuje w puli wątków w oczekiwaniu na żądania.</span><span class="sxs-lookup"><span data-stu-id="22a1d-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a1d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22a1d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22a1d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22a1d-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="22a1d-106">określoną Wskaźnik do minimalnej liczby bezczynnych wątków roboczych, które aktualnie przechowuje host.</span><span class="sxs-lookup"><span data-stu-id="22a1d-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22a1d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="22a1d-107">Return Value</span></span>  
  
|<span data-ttu-id="22a1d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22a1d-108">HRESULT</span></span>|<span data-ttu-id="22a1d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="22a1d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22a1d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="22a1d-110">S_OK</span></span>|<span data-ttu-id="22a1d-111">`GetMinThreads`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="22a1d-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="22a1d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22a1d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22a1d-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="22a1d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="22a1d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22a1d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22a1d-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="22a1d-115">The call timed out.</span></span>|  
|<span data-ttu-id="22a1d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22a1d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22a1d-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="22a1d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22a1d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22a1d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22a1d-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="22a1d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22a1d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22a1d-120">E_FAIL</span></span>|<span data-ttu-id="22a1d-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="22a1d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22a1d-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="22a1d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22a1d-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="22a1d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="22a1d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="22a1d-124">E_NOTIMPL</span></span>|<span data-ttu-id="22a1d-125">Host nie oferuje implementacji programu `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="22a1d-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22a1d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22a1d-126">Remarks</span></span>  
 <span data-ttu-id="22a1d-127">Host nie jest wymagany do zapewnienia implementacji programu `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="22a1d-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="22a1d-128">W takim przypadku powinna zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="22a1d-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22a1d-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22a1d-129">Requirements</span></span>  
 <span data-ttu-id="22a1d-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22a1d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22a1d-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="22a1d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22a1d-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="22a1d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22a1d-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22a1d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a1d-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22a1d-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="22a1d-135">GetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="22a1d-135">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="22a1d-136">SetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="22a1d-136">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="22a1d-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="22a1d-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
