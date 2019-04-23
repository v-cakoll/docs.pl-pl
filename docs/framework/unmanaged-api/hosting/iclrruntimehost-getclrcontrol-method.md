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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83b029c24321946f777966daa7a486f9e8e7b7a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073151"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="11b49-102">ICLRRuntimeHost::GetCLRControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="11b49-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="11b49-103">Pobiera wskaźnik interfejsu typu [iclrcontrol — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) czy hostów można użyć do dostosowania aspektów środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="11b49-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b49-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11b49-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11b49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11b49-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="11b49-106">[out] Wskaźnik interfejsu typu [iclrcontrol — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) umożliwiającej hostów skonfigurować dodatkowe aspekty środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="11b49-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11b49-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="11b49-107">Return Value</span></span>  
  
|<span data-ttu-id="11b49-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11b49-108">HRESULT</span></span>|<span data-ttu-id="11b49-109">Opis</span><span class="sxs-lookup"><span data-stu-id="11b49-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11b49-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="11b49-110">S_OK</span></span>|<span data-ttu-id="11b49-111">`GetCLRControl` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="11b49-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="11b49-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11b49-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11b49-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="11b49-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11b49-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11b49-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11b49-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="11b49-115">The call timed out.</span></span>|  
|<span data-ttu-id="11b49-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11b49-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11b49-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="11b49-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11b49-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11b49-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11b49-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="11b49-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11b49-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11b49-120">E_FAIL</span></span>|<span data-ttu-id="11b49-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="11b49-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11b49-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="11b49-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11b49-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11b49-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11b49-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="11b49-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="11b49-125">Środowisko CLR jest już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="11b49-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11b49-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11b49-126">Remarks</span></span>  
 <span data-ttu-id="11b49-127">`ICLRControl` udostępnia [getclrmanager — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody, która umożliwia hosta uzyskać wskaźnik interfejsu do jednego z typów menedżera.</span><span class="sxs-lookup"><span data-stu-id="11b49-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11b49-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11b49-128">Requirements</span></span>  
 <span data-ttu-id="11b49-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11b49-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11b49-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11b49-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11b49-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11b49-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11b49-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11b49-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b49-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11b49-133">See also</span></span>

- [<span data-ttu-id="11b49-134">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="11b49-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="11b49-135">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="11b49-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
