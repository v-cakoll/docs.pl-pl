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
ms.openlocfilehash: 71d4167d17b20c08c2cbc62d2ac0c1cddd88e527
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634443"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="1c3bc-102">ICLRRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c3bc-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="1c3bc-103">Zatrzymuje wykonywanie kodu przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="1c3bc-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1c3bc-104">Ta metoda nie zwolnienia zasobów na hoście, zwolnienie domeny aplikacji ani zniszczyć wątków.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="1c3bc-105">Musisz zakończyć procesu, aby zwolnić zasoby.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c3bc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c3bc-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1c3bc-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c3bc-107">Return Value</span></span>  
  
|<span data-ttu-id="1c3bc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c3bc-108">HRESULT</span></span>|<span data-ttu-id="1c3bc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1c3bc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c3bc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c3bc-110">S_OK</span></span>|<span data-ttu-id="1c3bc-111">`Stop` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="1c3bc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1c3bc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1c3bc-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1c3bc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1c3bc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1c3bc-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-115">The call timed out.</span></span>|  
|<span data-ttu-id="1c3bc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1c3bc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1c3bc-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1c3bc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1c3bc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1c3bc-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1c3bc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1c3bc-120">E_FAIL</span></span>|<span data-ttu-id="1c3bc-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1c3bc-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1c3bc-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1c3bc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c3bc-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c3bc-124">Requirements</span></span>  
 <span data-ttu-id="1c3bc-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c3bc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c3bc-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1c3bc-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c3bc-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c3bc-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c3bc-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c3bc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c3bc-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c3bc-129">See also</span></span>
- [<span data-ttu-id="1c3bc-130">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c3bc-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
