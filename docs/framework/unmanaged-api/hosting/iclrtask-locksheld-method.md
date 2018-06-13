---
title: ICLRTask::LocksHeld — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b49590fba64fc0372d671c009ad587b441e85343
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434232"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="64a53-102">ICLRTask::LocksHeld — Metoda</span><span class="sxs-lookup"><span data-stu-id="64a53-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="64a53-103">Pobiera liczbę blokad znajdujących się obecnie w zadania.</span><span class="sxs-lookup"><span data-stu-id="64a53-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a53-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64a53-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64a53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64a53-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="64a53-106">[out] Liczba blokady przechowywane w zadaniu w momencie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="64a53-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64a53-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="64a53-107">Return Value</span></span>  
  
|<span data-ttu-id="64a53-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64a53-108">HRESULT</span></span>|<span data-ttu-id="64a53-109">Opis</span><span class="sxs-lookup"><span data-stu-id="64a53-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64a53-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="64a53-110">S_OK</span></span>|<span data-ttu-id="64a53-111">`LocksHeld` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="64a53-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="64a53-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="64a53-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="64a53-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="64a53-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="64a53-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="64a53-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="64a53-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="64a53-115">The call timed out.</span></span>|  
|<span data-ttu-id="64a53-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="64a53-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="64a53-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="64a53-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="64a53-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="64a53-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="64a53-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="64a53-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="64a53-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="64a53-120">E_FAIL</span></span>|<span data-ttu-id="64a53-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="64a53-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="64a53-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="64a53-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="64a53-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="64a53-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64a53-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64a53-124">Requirements</span></span>  
 <span data-ttu-id="64a53-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64a53-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64a53-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="64a53-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64a53-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64a53-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64a53-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64a53-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a53-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64a53-129">See Also</span></span>  
 [<span data-ttu-id="64a53-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="64a53-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="64a53-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="64a53-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="64a53-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="64a53-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="64a53-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="64a53-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
