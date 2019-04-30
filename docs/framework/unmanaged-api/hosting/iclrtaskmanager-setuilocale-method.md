---
title: ICLRTaskManager::SetUILocale — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03c5c9d04567832951062fe1512a292f9b32a94b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763337"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="5bee4-102">ICLRTaskManager::SetUILocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="5bee4-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="5bee4-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR), czy host ma zmodyfikowane ustawienia regionalne interfejsu użytkownika lub kultury, na aktualnie przeprowadzane zadanie.</span><span class="sxs-lookup"><span data-stu-id="5bee4-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bee4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bee4-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bee4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bee4-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="5bee4-106">[in] Wartość identyfikatora ustawień regionalnych, który jest mapowany do nowo przypisanej kultury geograficzne i język interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5bee4-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bee4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5bee4-107">Return Value</span></span>  
  
|<span data-ttu-id="5bee4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5bee4-108">HRESULT</span></span>|<span data-ttu-id="5bee4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5bee4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5bee4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5bee4-110">S_OK</span></span>|<span data-ttu-id="5bee4-111">`SetUILocale` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="5bee4-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="5bee4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5bee4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5bee4-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="5bee4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5bee4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5bee4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5bee4-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="5bee4-115">The call timed out.</span></span>|  
|<span data-ttu-id="5bee4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5bee4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5bee4-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="5bee4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5bee4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5bee4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5bee4-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="5bee4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5bee4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5bee4-120">E_FAIL</span></span>|<span data-ttu-id="5bee4-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5bee4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5bee4-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="5bee4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5bee4-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5bee4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bee4-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5bee4-124">Remarks</span></span>  
 <span data-ttu-id="5bee4-125">`SetUILocale` zapewnia możliwość hosta do wykonywania jakichkolwiek mechanizmów środowiska użytkownika, który może mieć synchronizacji ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="5bee4-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bee4-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5bee4-126">Requirements</span></span>  
 <span data-ttu-id="5bee4-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bee4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bee4-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5bee4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5bee4-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5bee4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bee4-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bee4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bee4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bee4-131">See also</span></span>

- [<span data-ttu-id="5bee4-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bee4-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5bee4-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bee4-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5bee4-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bee4-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5bee4-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bee4-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
