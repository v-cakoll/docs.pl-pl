---
title: ICLRTask::Abort — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57efd4f29ba7e28adf1af03030d7f83eb32c1c2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139779"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="4514a-102">ICLRTask::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="4514a-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="4514a-103">Żądania, że środowisko uruchomieniowe języka wspólnego (CLR) przerwać zadanie, bieżący [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienie reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="4514a-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4514a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4514a-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4514a-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4514a-105">Return Value</span></span>  
  
|<span data-ttu-id="4514a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4514a-106">HRESULT</span></span>|<span data-ttu-id="4514a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4514a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4514a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4514a-108">S_OK</span></span>|`Abort` <span data-ttu-id="4514a-109">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="4514a-109">returned successfully.</span></span>|  
|<span data-ttu-id="4514a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4514a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4514a-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="4514a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4514a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4514a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4514a-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="4514a-113">The call timed out.</span></span>|  
|<span data-ttu-id="4514a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4514a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4514a-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="4514a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4514a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4514a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4514a-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="4514a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4514a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4514a-118">E_FAIL</span></span>|<span data-ttu-id="4514a-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4514a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4514a-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="4514a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4514a-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4514a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4514a-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4514a-122">Remarks</span></span>  
 <span data-ttu-id="4514a-123">Środowisko CLR wywołuje <xref:System.Threading.ThreadAbortException> kiedy wywołuje hosta `Abort`.</span><span class="sxs-lookup"><span data-stu-id="4514a-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="4514a-124">Zwraca natychmiast, po zainicjowaniu informacje o wyjątku, bez konieczności oczekiwania na kod użytkownika, takie jak finalizatory lub mechanizmy obsługi wyjątków, aby wykonać.</span><span class="sxs-lookup"><span data-stu-id="4514a-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="4514a-125">Wywołania `Abort` więc szybko zwracać wynik.</span><span class="sxs-lookup"><span data-stu-id="4514a-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4514a-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4514a-126">Requirements</span></span>  
 <span data-ttu-id="4514a-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4514a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4514a-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4514a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4514a-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4514a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4514a-130">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4514a-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4514a-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4514a-131">See also</span></span>

- [<span data-ttu-id="4514a-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4514a-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="4514a-133">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4514a-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4514a-134">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4514a-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4514a-135">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4514a-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
