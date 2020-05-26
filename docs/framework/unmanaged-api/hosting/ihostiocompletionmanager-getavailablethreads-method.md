---
title: IHostIoCompletionManager::GetAvailableThreads — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: 7ea7395bb1f185ba59940d76def562ab5440e560
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804768"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="29aac-102">IHostIoCompletionManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="29aac-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="29aac-103">Pobiera liczbę wątków zakończenia operacji we/wy (całkowitej liczby wątków zarządzanych przez hosta), które nie obsługują obecnie żądań.</span><span class="sxs-lookup"><span data-stu-id="29aac-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29aac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29aac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29aac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29aac-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="29aac-106">określoną Wskaźnik do liczby wątków zakończenia we/wy zarządzanych przez hosta, które są obecnie dostępne dla żądań obsługi.</span><span class="sxs-lookup"><span data-stu-id="29aac-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29aac-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="29aac-107">Return Value</span></span>  
  
|<span data-ttu-id="29aac-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29aac-108">HRESULT</span></span>|<span data-ttu-id="29aac-109">Opis</span><span class="sxs-lookup"><span data-stu-id="29aac-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29aac-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="29aac-110">S_OK</span></span>|<span data-ttu-id="29aac-111">`GetAvailableThreads`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="29aac-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="29aac-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29aac-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29aac-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="29aac-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="29aac-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="29aac-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="29aac-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="29aac-115">The call timed out.</span></span>|  
|<span data-ttu-id="29aac-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="29aac-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="29aac-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="29aac-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="29aac-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="29aac-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="29aac-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="29aac-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="29aac-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29aac-120">E_FAIL</span></span>|<span data-ttu-id="29aac-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="29aac-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="29aac-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="29aac-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="29aac-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="29aac-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="29aac-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="29aac-124">E_NOTIMPL</span></span>|<span data-ttu-id="29aac-125">Host nie oferuje implementacji programu `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="29aac-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29aac-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29aac-126">Remarks</span></span>  
 <span data-ttu-id="29aac-127">Host może potrzebować wyłącznej kontroli nad rozmiarem puli wątków ukończenia we/wy, z przyczyn takich jak implementacja, wydajność lub skalowalność.</span><span class="sxs-lookup"><span data-stu-id="29aac-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="29aac-128">W związku z tym host nie musi być zaimplementowany `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="29aac-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="29aac-129">W takim przypadku host powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="29aac-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29aac-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29aac-130">Requirements</span></span>  
 <span data-ttu-id="29aac-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29aac-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29aac-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="29aac-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29aac-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="29aac-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29aac-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29aac-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29aac-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29aac-135">See also</span></span>

- [<span data-ttu-id="29aac-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="29aac-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="29aac-137">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="29aac-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
