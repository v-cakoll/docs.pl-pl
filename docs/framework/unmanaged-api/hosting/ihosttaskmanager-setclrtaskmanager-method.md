---
title: IHostTaskManager::SetCLRTaskManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: 0e030a33a0a3368f35c82fad33f1ea2ce32446af
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841831"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="d140a-102">IHostTaskManager::SetCLRTaskManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="d140a-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="d140a-103">Udostępnia host ze wskaźnikiem interfejsu do wystąpienia [ICLRTaskManager](iclrtaskmanager-interface.md) zaimplementowanego przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d140a-103">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d140a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d140a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d140a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d140a-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="d140a-106">podczas Wskaźnik do `ICLRTaskManager` wystąpienia zaimplementowanego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="d140a-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d140a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d140a-107">Return Value</span></span>  
  
|<span data-ttu-id="d140a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d140a-108">HRESULT</span></span>|<span data-ttu-id="d140a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d140a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d140a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d140a-110">S_OK</span></span>|<span data-ttu-id="d140a-111">`SetCLRTaskManager`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="d140a-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="d140a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d140a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d140a-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d140a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d140a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d140a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d140a-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="d140a-115">The call timed out.</span></span>|  
|<span data-ttu-id="d140a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d140a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d140a-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d140a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d140a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d140a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d140a-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="d140a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d140a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d140a-120">E_FAIL</span></span>|<span data-ttu-id="d140a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d140a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d140a-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="d140a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d140a-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d140a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d140a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d140a-124">Remarks</span></span>  
 <span data-ttu-id="d140a-125">Wywołanie środowiska uruchomieniowego `SetCLRTaskManager` umożliwiające dostarczenie hosta za pomocą wskaźnika interfejsu do `ICLRTaskManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d140a-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d140a-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d140a-126">Requirements</span></span>  
 <span data-ttu-id="d140a-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d140a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d140a-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d140a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d140a-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d140a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d140a-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d140a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d140a-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d140a-131">See also</span></span>

- [<span data-ttu-id="d140a-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d140a-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d140a-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d140a-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d140a-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d140a-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d140a-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d140a-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
