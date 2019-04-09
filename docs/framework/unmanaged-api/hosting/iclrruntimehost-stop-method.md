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
ms.openlocfilehash: 85116244ad21842fab025ddd48106deef75f210b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166975"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="ef05f-102">ICLRRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef05f-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="ef05f-103">Zatrzymuje wykonywanie kodu przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ef05f-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef05f-104">Ta metoda nie zwolnienia zasobów na hoście, zwolnienie domeny aplikacji ani zniszczyć wątków.</span><span class="sxs-lookup"><span data-stu-id="ef05f-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="ef05f-105">Musisz zakończyć procesu, aby zwolnić zasoby.</span><span class="sxs-lookup"><span data-stu-id="ef05f-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef05f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef05f-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ef05f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ef05f-107">Return Value</span></span>  
  
|<span data-ttu-id="ef05f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef05f-108">HRESULT</span></span>|<span data-ttu-id="ef05f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ef05f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef05f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef05f-110">S_OK</span></span>|`Stop` <span data-ttu-id="ef05f-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="ef05f-111">returned successfully.</span></span>|  
|<span data-ttu-id="ef05f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef05f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef05f-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ef05f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef05f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef05f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef05f-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ef05f-115">The call timed out.</span></span>|  
|<span data-ttu-id="ef05f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef05f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef05f-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="ef05f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef05f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef05f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef05f-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ef05f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef05f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef05f-120">E_FAIL</span></span>|<span data-ttu-id="ef05f-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ef05f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef05f-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ef05f-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef05f-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ef05f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef05f-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef05f-124">Requirements</span></span>  
 <span data-ttu-id="ef05f-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef05f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef05f-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ef05f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef05f-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ef05f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ef05f-128">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ef05f-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef05f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef05f-129">See also</span></span>

- [<span data-ttu-id="ef05f-130">ICLRRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef05f-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
