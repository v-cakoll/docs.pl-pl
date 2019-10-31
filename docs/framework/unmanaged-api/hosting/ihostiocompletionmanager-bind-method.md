---
title: IHostIoCompletionManager::Bind — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
ms.openlocfilehash: 84fc99f6a5feb7ec73ee16942ba2794fc082dc89
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133898"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="dfc0a-102">IHostIoCompletionManager::Bind — Metoda</span><span class="sxs-lookup"><span data-stu-id="dfc0a-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="dfc0a-103">Wiąże określone dojście do portu zakończenia we/wy, który został utworzony przez wcześniejsze wywołanie do [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="dfc0a-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfc0a-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfc0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfc0a-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="dfc0a-106">podczas Port zakończenia we/wy, do którego ma zostać powiązany `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="dfc0a-107">Jeśli wartość `hPort` ma wartość null, `hHandle` jest powiązany z domyślnym portem zakończenia operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="dfc0a-108">podczas Dojście systemu operacyjnego do powiązania z `hPort`.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfc0a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dfc0a-109">Return Value</span></span>  
  
|<span data-ttu-id="dfc0a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfc0a-110">HRESULT</span></span>|<span data-ttu-id="dfc0a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="dfc0a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfc0a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfc0a-112">S_OK</span></span>|<span data-ttu-id="dfc0a-113">`Bind` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="dfc0a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dfc0a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dfc0a-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dfc0a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dfc0a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dfc0a-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-117">The call timed out.</span></span>|  
|<span data-ttu-id="dfc0a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dfc0a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dfc0a-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dfc0a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dfc0a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dfc0a-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dfc0a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dfc0a-122">E_FAIL</span></span>|<span data-ttu-id="dfc0a-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dfc0a-124">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dfc0a-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc0a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dfc0a-126">Remarks</span></span>  
 <span data-ttu-id="dfc0a-127">Port zakończenia we/wy jest tworzony przy użyciu wywołania do `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="dfc0a-128">Wywołania CLR `Bind`, aby powiązać dojście do tego portu.</span><span class="sxs-lookup"><span data-stu-id="dfc0a-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfc0a-129">Po zakończeniu żądania we/wy host musi wywołać metodę [ICLRIoCompletionManager:: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dfc0a-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc0a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfc0a-130">Requirements</span></span>  
 <span data-ttu-id="dfc0a-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfc0a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc0a-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dfc0a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfc0a-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dfc0a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfc0a-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc0a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc0a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfc0a-135">See also</span></span>

- [<span data-ttu-id="dfc0a-136">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dfc0a-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
