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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61f1938b114aee6d9084ccc68dce123b4924d1fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439471"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="628c9-102">IHostIoCompletionManager::SetMinThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="628c9-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="628c9-103">Ustawia minimalną liczbę wątków, które należy przyznać hosta do zakończenia operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="628c9-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="628c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="628c9-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="628c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="628c9-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="628c9-106">[in] Minimalna liczba wątków zakończenia We/Wy, które należy utworzyć hosta.</span><span class="sxs-lookup"><span data-stu-id="628c9-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="628c9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="628c9-107">Return Value</span></span>  
  
|<span data-ttu-id="628c9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="628c9-108">HRESULT</span></span>|<span data-ttu-id="628c9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="628c9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="628c9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="628c9-110">S_OK</span></span>|<span data-ttu-id="628c9-111">`SetMinThreads` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="628c9-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="628c9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="628c9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="628c9-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="628c9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="628c9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="628c9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="628c9-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="628c9-115">The call timed out.</span></span>|  
|<span data-ttu-id="628c9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="628c9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="628c9-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="628c9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="628c9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="628c9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="628c9-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="628c9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="628c9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="628c9-120">E_FAIL</span></span>|<span data-ttu-id="628c9-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="628c9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="628c9-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="628c9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="628c9-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="628c9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="628c9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="628c9-124">E_NOTIMPL</span></span>|<span data-ttu-id="628c9-125">Host nie zapewniać implementację elementu `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="628c9-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="628c9-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="628c9-126">Remarks</span></span>  
 <span data-ttu-id="628c9-127">Host może być wyłączną kontrolę nad to liczba wątków, które może być przydzielona do przetwarzania żądań We/Wy, powodów, takich jak wdrożenia, wydajności i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="628c9-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="628c9-128">Z tego powodu hosta nie jest wymagane do zaimplementowania `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="628c9-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="628c9-129">W takim przypadku hosta powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="628c9-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="628c9-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="628c9-130">Requirements</span></span>  
 <span data-ttu-id="628c9-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="628c9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="628c9-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="628c9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="628c9-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="628c9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="628c9-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="628c9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="628c9-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="628c9-135">See Also</span></span>  
 [<span data-ttu-id="628c9-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="628c9-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="628c9-137">SetMaxThreads, metoda</span><span class="sxs-lookup"><span data-stu-id="628c9-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="628c9-138">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="628c9-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
