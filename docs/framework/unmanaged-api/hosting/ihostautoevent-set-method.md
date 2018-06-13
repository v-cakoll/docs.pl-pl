---
title: IHostAutoEvent::Set — Metoda
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a5972ad555b6c3286777b5da79598fc7f1239b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438630"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="e4caf-102">IHostAutoEvent::Set — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4caf-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="e4caf-103">Ustawia bieżący [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienia sygnałowego stanu.</span><span class="sxs-lookup"><span data-stu-id="e4caf-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4caf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4caf-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e4caf-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e4caf-105">Return Value</span></span>  
  
|<span data-ttu-id="e4caf-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4caf-106">HRESULT</span></span>|<span data-ttu-id="e4caf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e4caf-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4caf-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4caf-108">S_OK</span></span>|<span data-ttu-id="e4caf-109">`Set` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e4caf-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="e4caf-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4caf-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4caf-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e4caf-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4caf-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4caf-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4caf-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e4caf-113">The call timed out.</span></span>|  
|<span data-ttu-id="e4caf-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4caf-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4caf-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e4caf-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4caf-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4caf-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4caf-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e4caf-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4caf-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4caf-118">E_FAIL</span></span>|<span data-ttu-id="e4caf-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e4caf-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4caf-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e4caf-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4caf-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e4caf-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4caf-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4caf-122">Requirements</span></span>  
 <span data-ttu-id="e4caf-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4caf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4caf-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4caf-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4caf-125">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4caf-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4caf-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4caf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4caf-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4caf-127">See Also</span></span>  
 [<span data-ttu-id="e4caf-128">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4caf-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e4caf-129">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4caf-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="e4caf-130">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4caf-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="e4caf-131">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4caf-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
