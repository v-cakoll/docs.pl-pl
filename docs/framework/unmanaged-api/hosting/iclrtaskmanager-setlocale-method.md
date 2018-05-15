---
title: ICLRTaskManager::SetLocale — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab6b13c6b7dba34f5ea82d05f483b36bf96aab1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="6cab9-102">ICLRTaskManager::SetLocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="6cab9-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="6cab9-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR), czy host został zmodyfikowany wartość identyfikatora ustawień regionalnych (który mapuje, kultury geograficzne i języka) aktualnie wykonywanego zadania.</span><span class="sxs-lookup"><span data-stu-id="6cab9-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cab9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6cab9-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cab9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cab9-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="6cab9-106">[in] Wartość identyfikatora ustawień regionalnych mapy do nowo przypisanej kultury geograficzne i języka.</span><span class="sxs-lookup"><span data-stu-id="6cab9-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cab9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6cab9-107">Return Value</span></span>  
  
|<span data-ttu-id="6cab9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cab9-108">HRESULT</span></span>|<span data-ttu-id="6cab9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6cab9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6cab9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6cab9-110">S_OK</span></span>|<span data-ttu-id="6cab9-111">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6cab9-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="6cab9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6cab9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6cab9-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6cab9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6cab9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6cab9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6cab9-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6cab9-115">The call timed out.</span></span>|  
|<span data-ttu-id="6cab9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6cab9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6cab9-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="6cab9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6cab9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6cab9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6cab9-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6cab9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6cab9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6cab9-120">E_FAIL</span></span>|<span data-ttu-id="6cab9-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6cab9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6cab9-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6cab9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6cab9-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6cab9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cab9-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cab9-124">Remarks</span></span>  
 <span data-ttu-id="6cab9-125">`SetLocale` zapewnia możliwość wykonywania jakichkolwiek mechanizmów, który może mieć synchronizacji ustawień regionalnych hosta.</span><span class="sxs-lookup"><span data-stu-id="6cab9-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cab9-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6cab9-126">Requirements</span></span>  
 <span data-ttu-id="6cab9-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cab9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cab9-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cab9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cab9-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cab9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cab9-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cab9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cab9-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cab9-131">See Also</span></span>  
 [<span data-ttu-id="6cab9-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cab9-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="6cab9-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cab9-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="6cab9-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cab9-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="6cab9-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cab9-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
