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
ms.openlocfilehash: 97a0e6cbbd8972f58f9eedcfeb8aff1f93694064
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765673"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="a15bc-102">ICLRRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="a15bc-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="a15bc-103">Zatrzymuje wykonywanie kodu przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a15bc-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a15bc-104">Ta metoda nie zwolnienia zasobów na hoście, zwolnienie domeny aplikacji ani zniszczyć wątków.</span><span class="sxs-lookup"><span data-stu-id="a15bc-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="a15bc-105">Musisz zakończyć procesu, aby zwolnić zasoby.</span><span class="sxs-lookup"><span data-stu-id="a15bc-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a15bc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a15bc-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a15bc-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a15bc-107">Return Value</span></span>  
  
|<span data-ttu-id="a15bc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a15bc-108">HRESULT</span></span>|<span data-ttu-id="a15bc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a15bc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a15bc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a15bc-110">S_OK</span></span>|<span data-ttu-id="a15bc-111">`Stop` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a15bc-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="a15bc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a15bc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a15bc-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a15bc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a15bc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a15bc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a15bc-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a15bc-115">The call timed out.</span></span>|  
|<span data-ttu-id="a15bc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a15bc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a15bc-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a15bc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a15bc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a15bc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a15bc-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a15bc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a15bc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a15bc-120">E_FAIL</span></span>|<span data-ttu-id="a15bc-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a15bc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a15bc-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a15bc-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a15bc-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a15bc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a15bc-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a15bc-124">Requirements</span></span>  
 <span data-ttu-id="a15bc-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a15bc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a15bc-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a15bc-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a15bc-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a15bc-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a15bc-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a15bc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a15bc-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a15bc-129">See also</span></span>

- [<span data-ttu-id="a15bc-130">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="a15bc-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
