---
title: IHostIoCompletionManager::GetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
ms.openlocfilehash: a97a7abf4f561a5aba41d8019f2ba5bd8e879acd
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804736"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="1743a-102">IHostIoCompletionManager::GetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="1743a-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="1743a-103">Pobiera maksymalną liczbę wątków, które host może przydzielić do żądań we/wy usługi.</span><span class="sxs-lookup"><span data-stu-id="1743a-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1743a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1743a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1743a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1743a-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="1743a-106">określoną Wskaźnik do maksymalnej liczby wątków w puli wątków, które host może przydzielić do obsługi żądań we/wy usługi.</span><span class="sxs-lookup"><span data-stu-id="1743a-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1743a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1743a-107">Return Value</span></span>  
  
|<span data-ttu-id="1743a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1743a-108">HRESULT</span></span>|<span data-ttu-id="1743a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1743a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1743a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1743a-110">S_OK</span></span>|<span data-ttu-id="1743a-111">`GetMaxThreads`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="1743a-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="1743a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1743a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1743a-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1743a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1743a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1743a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1743a-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="1743a-115">The call timed out.</span></span>|  
|<span data-ttu-id="1743a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1743a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1743a-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1743a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1743a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1743a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1743a-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="1743a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1743a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1743a-120">E_FAIL</span></span>|<span data-ttu-id="1743a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1743a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1743a-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="1743a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1743a-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1743a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1743a-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1743a-124">E_NOTIMPL</span></span>|<span data-ttu-id="1743a-125">Host nie oferuje implementacji programu `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="1743a-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1743a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1743a-126">Remarks</span></span>  
 <span data-ttu-id="1743a-127">Host może potrzebować wyłącznej kontroli nad liczbą wątków, które mogą być przydzielone do przetwarzania żądań we/wy, z przyczyn takich jak implementacja, wydajność lub skalowalność.</span><span class="sxs-lookup"><span data-stu-id="1743a-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="1743a-128">Z tego powodu host nie musi być zaimplementowany `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="1743a-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="1743a-129">W takim przypadku host powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="1743a-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1743a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1743a-130">Requirements</span></span>  
 <span data-ttu-id="1743a-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1743a-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1743a-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1743a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1743a-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1743a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1743a-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1743a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1743a-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1743a-135">See also</span></span>

- [<span data-ttu-id="1743a-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1743a-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1743a-137">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1743a-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
