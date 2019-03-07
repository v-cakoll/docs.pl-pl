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
ms.openlocfilehash: afe3cb631590964e9b5e9acff471f4b15491eabc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500281"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="d1266-102">ICLRTaskManager::SetLocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1266-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="d1266-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR), czy host został zmodyfikowany wartość identyfikatora ustawień regionalnych (który mapuje geograficzne kultury i języka) aktualnie przeprowadzane zadanie.</span><span class="sxs-lookup"><span data-stu-id="d1266-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1266-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1266-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1266-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1266-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="d1266-106">[in] Wartość identyfikatora ustawień regionalnych, który jest mapowany do nowo przypisanej geograficzne kultury i języka.</span><span class="sxs-lookup"><span data-stu-id="d1266-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1266-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1266-107">Return Value</span></span>  
  
|<span data-ttu-id="d1266-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1266-108">HRESULT</span></span>|<span data-ttu-id="d1266-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d1266-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1266-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1266-110">S_OK</span></span>|<span data-ttu-id="d1266-111">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d1266-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="d1266-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1266-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1266-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d1266-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d1266-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1266-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1266-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d1266-115">The call timed out.</span></span>|  
|<span data-ttu-id="d1266-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1266-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1266-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d1266-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1266-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1266-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1266-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d1266-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1266-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1266-120">E_FAIL</span></span>|<span data-ttu-id="d1266-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d1266-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1266-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d1266-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1266-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d1266-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1266-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1266-124">Remarks</span></span>  
 <span data-ttu-id="d1266-125">`SetLocale` Umożliwia hosta do wykonywania jakichkolwiek mechanizmów środowiska użytkownika, który może mieć synchronizacji ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="d1266-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1266-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1266-126">Requirements</span></span>  
 <span data-ttu-id="d1266-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1266-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1266-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1266-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1266-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1266-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1266-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1266-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1266-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1266-131">See also</span></span>
- [<span data-ttu-id="d1266-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1266-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d1266-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1266-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d1266-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1266-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d1266-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1266-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
