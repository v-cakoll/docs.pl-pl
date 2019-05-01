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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4f16db1d35f8a0de1c755566e27b07bf9067dfe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796594"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="017f3-102">IHostThreadPoolManager::GetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="017f3-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="017f3-103">Pobiera liczbę wątków w puli wątków, które nie są obecnie przetwarza elementy robocze.</span><span class="sxs-lookup"><span data-stu-id="017f3-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="017f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="017f3-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="017f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="017f3-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="017f3-106">[out] Wskaźnik do liczby wątków w puli wątków, które nie są obecnie przetwarza elementy robocze.</span><span class="sxs-lookup"><span data-stu-id="017f3-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="017f3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="017f3-107">Return Value</span></span>  
  
|<span data-ttu-id="017f3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="017f3-108">HRESULT</span></span>|<span data-ttu-id="017f3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="017f3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="017f3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="017f3-110">S_OK</span></span>|<span data-ttu-id="017f3-111">`GetAvailableThreads` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="017f3-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="017f3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="017f3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="017f3-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="017f3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="017f3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="017f3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="017f3-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="017f3-115">The call timed out.</span></span>|  
|<span data-ttu-id="017f3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="017f3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="017f3-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="017f3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="017f3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="017f3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="017f3-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="017f3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="017f3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="017f3-120">E_FAIL</span></span>|<span data-ttu-id="017f3-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="017f3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="017f3-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="017f3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="017f3-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="017f3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="017f3-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="017f3-124">E_NOTIMPL</span></span>|<span data-ttu-id="017f3-125">Host nie zawiera implementacji `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="017f3-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="017f3-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="017f3-126">Remarks</span></span>  
 <span data-ttu-id="017f3-127">Jeśli host nie dostarcza implementację `GetAvailableThreads`, powinna zwrócić wartość HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="017f3-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="017f3-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="017f3-128">Requirements</span></span>  
 <span data-ttu-id="017f3-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="017f3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="017f3-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="017f3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="017f3-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="017f3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="017f3-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="017f3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017f3-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="017f3-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="017f3-134">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="017f3-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
