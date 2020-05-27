---
title: IHostIoCompletionManager::CloseIoCompletionPort — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: 5e2e49b4c993e127a31b54d40f721e0714198780
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804780"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="2f1a5-102">IHostIoCompletionManager::CloseIoCompletionPort — Metoda</span><span class="sxs-lookup"><span data-stu-id="2f1a5-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="2f1a5-103">Żąda zamknięcia przez hosta portu, który został otwarty za pomocą wcześniejszego wywołania do [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="2f1a5-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f1a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f1a5-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f1a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f1a5-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="2f1a5-106">podczas Dojście portu do zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f1a5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2f1a5-107">Return Value</span></span>  
  
|<span data-ttu-id="2f1a5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f1a5-108">HRESULT</span></span>|<span data-ttu-id="2f1a5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2f1a5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f1a5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f1a5-110">S_OK</span></span>|<span data-ttu-id="2f1a5-111">`CloseIoCompletionPort`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="2f1a5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f1a5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f1a5-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f1a5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f1a5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f1a5-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-115">The call timed out.</span></span>|  
|<span data-ttu-id="2f1a5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f1a5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f1a5-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f1a5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f1a5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f1a5-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f1a5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f1a5-120">E_FAIL</span></span>|<span data-ttu-id="2f1a5-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f1a5-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f1a5-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2f1a5-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2f1a5-124">E_INVALIDARG</span></span>|<span data-ttu-id="2f1a5-125">Przekazano nieprawidłowe dojście do portu.</span><span class="sxs-lookup"><span data-stu-id="2f1a5-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f1a5-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f1a5-126">Remarks</span></span>  
 <span data-ttu-id="2f1a5-127">`hPort`musi być dojściem do portu, który został utworzony przy użyciu wcześniejszego wywołania do `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="2f1a5-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f1a5-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f1a5-128">Requirements</span></span>  
 <span data-ttu-id="2f1a5-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f1a5-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f1a5-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f1a5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f1a5-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f1a5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f1a5-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f1a5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f1a5-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f1a5-133">See also</span></span>

- [<span data-ttu-id="2f1a5-134">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f1a5-134">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="2f1a5-135">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f1a5-135">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
