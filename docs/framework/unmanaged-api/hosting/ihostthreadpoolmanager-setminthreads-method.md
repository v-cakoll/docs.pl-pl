---
title: IHostThreadPoolManager::SetMinThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
ms.openlocfilehash: c5b150b161acba3820ced367049f08153dd091aa
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842442"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="33a3a-102">IHostThreadPoolManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="33a3a-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="33a3a-103">Określa minimalną liczbę bezczynnych wątków, które host musi zachować w oczekiwaniu na żądania.</span><span class="sxs-lookup"><span data-stu-id="33a3a-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33a3a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33a3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33a3a-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="33a3a-106">podczas Nowa minimalna liczba wątków, które host musi zachować.</span><span class="sxs-lookup"><span data-stu-id="33a3a-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33a3a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33a3a-107">Return Value</span></span>  
  
|<span data-ttu-id="33a3a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33a3a-108">HRESULT</span></span>|<span data-ttu-id="33a3a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="33a3a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33a3a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="33a3a-110">S_OK</span></span>|<span data-ttu-id="33a3a-111">`SetMinThreads`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="33a3a-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="33a3a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="33a3a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="33a3a-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="33a3a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="33a3a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="33a3a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="33a3a-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="33a3a-115">The call timed out.</span></span>|  
|<span data-ttu-id="33a3a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="33a3a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="33a3a-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="33a3a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="33a3a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="33a3a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="33a3a-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="33a3a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="33a3a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33a3a-120">E_FAIL</span></span>|<span data-ttu-id="33a3a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="33a3a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="33a3a-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="33a3a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="33a3a-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="33a3a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="33a3a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="33a3a-124">E_NOTIMPL</span></span>|<span data-ttu-id="33a3a-125">Host nie oferuje implementacji programu `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="33a3a-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33a3a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33a3a-126">Remarks</span></span>  
 <span data-ttu-id="33a3a-127">Host nie jest wymagany do zapewnienia implementacji programu `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="33a3a-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="33a3a-128">W takim przypadku powinna zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="33a3a-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33a3a-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33a3a-129">Requirements</span></span>  
 <span data-ttu-id="33a3a-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33a3a-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a3a-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="33a3a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33a3a-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="33a3a-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33a3a-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33a3a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a3a-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33a3a-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="33a3a-135">GetMinThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="33a3a-135">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="33a3a-136">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="33a3a-136">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="33a3a-137">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="33a3a-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
