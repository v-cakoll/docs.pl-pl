---
title: IHostIoCompletionManager::SetMinThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: 29a2fc5652badcc00378192debccba0356f5339e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804656"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="4bf25-102">IHostIoCompletionManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="4bf25-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="4bf25-103">Ustawia minimalną liczbę wątków, które host powinien przydzielić do zakończenia operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="4bf25-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bf25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bf25-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bf25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bf25-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="4bf25-106">podczas Minimalna liczba wątków zakończenia we/wy, które powinien utworzyć host.</span><span class="sxs-lookup"><span data-stu-id="4bf25-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bf25-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4bf25-107">Return Value</span></span>  
  
|<span data-ttu-id="4bf25-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bf25-108">HRESULT</span></span>|<span data-ttu-id="4bf25-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4bf25-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bf25-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bf25-110">S_OK</span></span>|<span data-ttu-id="4bf25-111">`SetMinThreads`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="4bf25-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4bf25-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bf25-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bf25-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4bf25-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4bf25-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4bf25-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4bf25-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="4bf25-115">The call timed out.</span></span>|  
|<span data-ttu-id="4bf25-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4bf25-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4bf25-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="4bf25-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4bf25-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4bf25-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4bf25-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="4bf25-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4bf25-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bf25-120">E_FAIL</span></span>|<span data-ttu-id="4bf25-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4bf25-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4bf25-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="4bf25-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4bf25-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4bf25-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4bf25-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4bf25-124">E_NOTIMPL</span></span>|<span data-ttu-id="4bf25-125">Host nie oferuje implementacji programu `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="4bf25-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bf25-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bf25-126">Remarks</span></span>  
 <span data-ttu-id="4bf25-127">Host może potrzebować wyłącznej kontroli nad liczbą wątków, które mogą być przydzielone do przetwarzania żądań we/wy, z przyczyn takich jak implementacja, wydajność lub skalowalność.</span><span class="sxs-lookup"><span data-stu-id="4bf25-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="4bf25-128">Z tego powodu host nie musi być zaimplementowany `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="4bf25-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="4bf25-129">W takim przypadku host powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="4bf25-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bf25-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4bf25-130">Requirements</span></span>  
 <span data-ttu-id="4bf25-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bf25-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bf25-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4bf25-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bf25-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4bf25-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bf25-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bf25-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf25-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4bf25-135">See also</span></span>

- [<span data-ttu-id="4bf25-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4bf25-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="4bf25-137">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="4bf25-137">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="4bf25-138">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4bf25-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
