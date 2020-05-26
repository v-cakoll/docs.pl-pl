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
ms.openlocfilehash: 74ffc5c92402808ae566d7cb014d9d920c384ae8
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804948"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="ca421-102">IHostControl::SetAppDomainManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca421-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="ca421-103">Powiadamia hosta o utworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca421-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca421-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca421-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca421-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca421-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="ca421-106">podczas Liczbowy identyfikator wybranego elementu <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ca421-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="ca421-107">podczas Wskaźnik do <xref:System.AppDomainManager> obiektu, który jest implementowany przez hosta `IUnknown` .</span><span class="sxs-lookup"><span data-stu-id="ca421-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca421-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ca421-108">Return Value</span></span>  
  
|<span data-ttu-id="ca421-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca421-109">HRESULT</span></span>|<span data-ttu-id="ca421-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ca421-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca421-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca421-111">S_OK</span></span>|<span data-ttu-id="ca421-112">`SetAppDomainManager`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="ca421-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="ca421-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca421-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca421-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ca421-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca421-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca421-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca421-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ca421-116">The call timed out.</span></span>|  
|<span data-ttu-id="ca421-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca421-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca421-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ca421-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca421-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca421-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca421-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ca421-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca421-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca421-121">E_FAIL</span></span>|<span data-ttu-id="ca421-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ca421-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca421-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="ca421-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca421-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca421-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca421-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca421-125">Remarks</span></span>  
 <span data-ttu-id="ca421-126"><xref:System.AppDomainManager>Zapewnia host z mechanizmem ładowania do kodu zarządzanego i kontrolowania tworzenia i ustawień każdego z nich <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ca421-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="ca421-127"><xref:System.AppDomainManager>Jest ładowany do każdego <xref:System.AppDomain> , kiedy <xref:System.AppDomain> jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="ca421-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="ca421-128">W przypadku wybrania tej opcji środowisko CLR powiadamia hosta o utworzeniu domeny aplikacji przez ustawienie wartości `pUnkAppDomainManager` parametru.</span><span class="sxs-lookup"><span data-stu-id="ca421-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="ca421-129">We wdrożeniu `SetAppDomainManager` metody, host może ustawić nazwę zestawu i typ dla Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca421-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca421-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca421-130">Requirements</span></span>  
 <span data-ttu-id="ca421-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca421-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca421-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ca421-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca421-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca421-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca421-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca421-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca421-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca421-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="ca421-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca421-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
