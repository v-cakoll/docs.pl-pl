---
title: ICLRRuntimeHost::GetCLRControl — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
ms.openlocfilehash: 478e07f18d40043de4e800c36647ac4a32499635
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120430"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="38730-102">ICLRRuntimeHost::GetCLRControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="38730-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="38730-103">Pobiera wskaźnik interfejsu typu [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , który może być używany przez hosty do dostosowywania aspektów środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="38730-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38730-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38730-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38730-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38730-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="38730-106">określoną Wskaźnik interfejsu typu [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , który umożliwia hostom Konfigurowanie dodatkowych aspektów środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="38730-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38730-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="38730-107">Return Value</span></span>  
  
|<span data-ttu-id="38730-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38730-108">HRESULT</span></span>|<span data-ttu-id="38730-109">Opis</span><span class="sxs-lookup"><span data-stu-id="38730-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38730-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="38730-110">S_OK</span></span>|<span data-ttu-id="38730-111">`GetCLRControl` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="38730-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="38730-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38730-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38730-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="38730-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38730-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38730-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38730-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="38730-115">The call timed out.</span></span>|  
|<span data-ttu-id="38730-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38730-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38730-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="38730-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38730-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38730-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38730-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="38730-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38730-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38730-120">E_FAIL</span></span>|<span data-ttu-id="38730-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="38730-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38730-122">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="38730-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38730-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38730-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="38730-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="38730-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="38730-125">Środowisko CLR zostało już uruchomione.</span><span class="sxs-lookup"><span data-stu-id="38730-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38730-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38730-126">Remarks</span></span>  
 <span data-ttu-id="38730-127">`ICLRControl` udostępnia metodę [metody GetCLRManager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) , która umożliwia hostowi uzyskanie wskaźnika interfejsu do jednego z typów Menedżera.</span><span class="sxs-lookup"><span data-stu-id="38730-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38730-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38730-128">Requirements</span></span>  
 <span data-ttu-id="38730-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38730-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38730-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="38730-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38730-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38730-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38730-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38730-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38730-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38730-133">See also</span></span>

- [<span data-ttu-id="38730-134">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="38730-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="38730-135">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="38730-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
