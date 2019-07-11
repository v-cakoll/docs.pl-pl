---
title: IHostControl::SetAppDomainManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94deb4eaeeec2400aebf397d391ce4b67c16989e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763884"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="11172-102">IHostControl::SetAppDomainManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="11172-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="11172-103">Powiadamia hosta, że utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11172-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11172-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11172-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11172-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11172-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="11172-106">[in] Identyfikator liczbowy wybranego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="11172-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="11172-107">[in] Wskaźnik do <xref:System.AppDomainManager> obiektu implementującego hosta jako `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="11172-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11172-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="11172-108">Return Value</span></span>  
  
|<span data-ttu-id="11172-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11172-109">HRESULT</span></span>|<span data-ttu-id="11172-110">Opis</span><span class="sxs-lookup"><span data-stu-id="11172-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11172-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="11172-111">S_OK</span></span>|<span data-ttu-id="11172-112">`SetAppDomainManager` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="11172-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="11172-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11172-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11172-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="11172-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11172-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11172-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11172-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="11172-116">The call timed out.</span></span>|  
|<span data-ttu-id="11172-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11172-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11172-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="11172-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11172-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11172-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11172-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="11172-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11172-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11172-121">E_FAIL</span></span>|<span data-ttu-id="11172-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="11172-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11172-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="11172-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11172-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11172-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11172-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11172-125">Remarks</span></span>  
 <span data-ttu-id="11172-126"><xref:System.AppDomainManager> Udostępnia mechanizm do uruchamiania kodu zarządzanego i sterowania tworzenia i ustawienia każdego hosta <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="11172-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="11172-127"><xref:System.AppDomainManager> Jest ładowany do każdego <xref:System.AppDomain> podczas który <xref:System.AppDomain> zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="11172-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="11172-128">Jeśli go wybierze, środowisko CLR powiadamia hosta, czy domena aplikacji została utworzona, ustawiając wartość `pUnkAppDomainManager` parametru.</span><span class="sxs-lookup"><span data-stu-id="11172-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="11172-129">W jego implementacja obiektu `SetAppDomainManager` metody hosta można ustawić nazwy zestawu i typu dla Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11172-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11172-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11172-130">Requirements</span></span>  
 <span data-ttu-id="11172-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11172-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11172-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11172-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11172-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11172-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11172-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11172-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11172-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11172-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="11172-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="11172-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
