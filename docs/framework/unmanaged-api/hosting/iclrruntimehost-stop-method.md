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
ms.openlocfilehash: 0b59532d18848f1896977aa37f0a9f54a939aa75
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120375"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="a0c6b-102">ICLRRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0c6b-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="a0c6b-103">Kończy wykonywanie kodu przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a0c6b-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a0c6b-104">Ta metoda nie zwalnia zasobów dla hosta, zwalnia domen aplikacji lub niszczy wątki.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="a0c6b-105">Musisz zakończyć proces, aby zwolnić te zasoby.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c6b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0c6b-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a0c6b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0c6b-107">Return Value</span></span>  
  
|<span data-ttu-id="a0c6b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0c6b-108">HRESULT</span></span>|<span data-ttu-id="a0c6b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a0c6b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0c6b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0c6b-110">S_OK</span></span>|<span data-ttu-id="a0c6b-111">`Stop` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="a0c6b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0c6b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0c6b-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0c6b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0c6b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0c6b-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-115">The call timed out.</span></span>|  
|<span data-ttu-id="a0c6b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0c6b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0c6b-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0c6b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0c6b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0c6b-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0c6b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0c6b-120">E_FAIL</span></span>|<span data-ttu-id="a0c6b-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0c6b-122">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0c6b-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a0c6b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0c6b-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0c6b-124">Requirements</span></span>  
 <span data-ttu-id="a0c6b-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0c6b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0c6b-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a0c6b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0c6b-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a0c6b-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0c6b-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0c6b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c6b-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0c6b-129">See also</span></span>

- [<span data-ttu-id="a0c6b-130">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0c6b-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
