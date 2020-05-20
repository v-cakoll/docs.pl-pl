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
ms.openlocfilehash: 55cd444ffedc92ba74239421ae548ffd930e6ab7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703934"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="026f7-102">ICLRRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="026f7-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="026f7-103">Kończy wykonywanie kodu przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="026f7-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="026f7-104">Ta metoda nie zwalnia zasobów dla hosta, zwalnia domen aplikacji lub niszczy wątki.</span><span class="sxs-lookup"><span data-stu-id="026f7-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="026f7-105">Musisz zakończyć proces, aby zwolnić te zasoby.</span><span class="sxs-lookup"><span data-stu-id="026f7-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="026f7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="026f7-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="026f7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="026f7-107">Return Value</span></span>  
  
|<span data-ttu-id="026f7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="026f7-108">HRESULT</span></span>|<span data-ttu-id="026f7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="026f7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="026f7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="026f7-110">S_OK</span></span>|<span data-ttu-id="026f7-111">`Stop`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="026f7-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="026f7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="026f7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="026f7-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="026f7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="026f7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="026f7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="026f7-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="026f7-115">The call timed out.</span></span>|  
|<span data-ttu-id="026f7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="026f7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="026f7-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="026f7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="026f7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="026f7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="026f7-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="026f7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="026f7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="026f7-120">E_FAIL</span></span>|<span data-ttu-id="026f7-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="026f7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="026f7-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="026f7-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="026f7-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="026f7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="026f7-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="026f7-124">Requirements</span></span>  
 <span data-ttu-id="026f7-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="026f7-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="026f7-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="026f7-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="026f7-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="026f7-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="026f7-128">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="026f7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="026f7-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="026f7-129">See also</span></span>

- [<span data-ttu-id="026f7-130">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="026f7-130">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
