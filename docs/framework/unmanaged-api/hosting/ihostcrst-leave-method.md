---
title: IHostCrst::Leave — Metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae5561abb7cd0770fd5b7f290a4aa8dff85b6150
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441655"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="a6118-102">IHostCrst::Leave — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6118-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="a6118-103">Pozostawia sekcja krytyczna, reprezentowanego przez bieżące wystąpienie klasy [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a6118-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6118-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6118-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a6118-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a6118-105">Return Value</span></span>  
  
|<span data-ttu-id="a6118-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6118-106">HRESULT</span></span>|<span data-ttu-id="a6118-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a6118-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6118-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6118-108">S_OK</span></span>|<span data-ttu-id="a6118-109">`Leave` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a6118-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="a6118-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a6118-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6118-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a6118-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a6118-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a6118-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a6118-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a6118-113">The call timed out.</span></span>|  
|<span data-ttu-id="a6118-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a6118-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a6118-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a6118-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a6118-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a6118-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a6118-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a6118-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a6118-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6118-118">E_FAIL</span></span>|<span data-ttu-id="a6118-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a6118-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a6118-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a6118-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a6118-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a6118-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6118-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6118-122">Remarks</span></span>  
 <span data-ttu-id="a6118-123">`Leave` Umożliwia środowisko CLR, które komunikują się bezpośrednio z hosta wątkowość implementacji, a nie przy użyciu odpowiedniego Win32 `LeaveCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="a6118-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="a6118-124">Wątku, który przejmuje sekcja krytyczna reprezentowany przez bieżący `IHostCrst` należy wywołać metodę wystąpienia `Leave` po za każdym razem, wejdzie ona tej sekcji krytycznych.</span><span class="sxs-lookup"><span data-stu-id="a6118-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6118-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6118-125">Requirements</span></span>  
 <span data-ttu-id="a6118-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6118-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6118-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a6118-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6118-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6118-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6118-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6118-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6118-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6118-130">See Also</span></span>  
 [<span data-ttu-id="a6118-131">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6118-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="a6118-132">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6118-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="a6118-133">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6118-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
