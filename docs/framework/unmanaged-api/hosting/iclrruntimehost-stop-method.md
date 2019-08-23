---
title: ICLRRuntimeHost::Stop — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fcadb708638efb0b7946426c538e01661505dfa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912240"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="4a5f9-102">ICLRRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a5f9-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="4a5f9-103">Kończy wykonywanie kodu przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="4a5f9-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4a5f9-104">Ta metoda nie zwalnia zasobów dla hosta, zwalnia domen aplikacji lub niszczy wątki.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="4a5f9-105">Musisz zakończyć proces, aby zwolnić te zasoby.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a5f9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a5f9-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4a5f9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4a5f9-107">Return Value</span></span>  
  
|<span data-ttu-id="4a5f9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a5f9-108">HRESULT</span></span>|<span data-ttu-id="4a5f9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4a5f9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a5f9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a5f9-110">S_OK</span></span>|<span data-ttu-id="4a5f9-111">`Stop`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="4a5f9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a5f9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a5f9-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a5f9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a5f9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a5f9-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-115">The call timed out.</span></span>|  
|<span data-ttu-id="4a5f9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a5f9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a5f9-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a5f9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a5f9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a5f9-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a5f9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a5f9-120">E_FAIL</span></span>|<span data-ttu-id="4a5f9-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a5f9-122">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a5f9-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4a5f9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a5f9-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a5f9-124">Requirements</span></span>  
 <span data-ttu-id="4a5f9-125">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a5f9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a5f9-126">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4a5f9-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a5f9-127">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4a5f9-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a5f9-128">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a5f9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5f9-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a5f9-129">See also</span></span>

- [<span data-ttu-id="4a5f9-130">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a5f9-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
