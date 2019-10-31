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
ms.openlocfilehash: de264135450190fd028eb8cf12017d94cc65ffac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134722"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="a097a-102">IHostControl::SetAppDomainManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="a097a-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="a097a-103">Powiadamia hosta o utworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a097a-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a097a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a097a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a097a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a097a-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="a097a-106">podczas Liczbowy identyfikator wybranego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a097a-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="a097a-107">podczas Wskaźnik do obiektu <xref:System.AppDomainManager>, który jest implementowany przez hosta jako `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="a097a-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a097a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a097a-108">Return Value</span></span>  
  
|<span data-ttu-id="a097a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a097a-109">HRESULT</span></span>|<span data-ttu-id="a097a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a097a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a097a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a097a-111">S_OK</span></span>|<span data-ttu-id="a097a-112">`SetAppDomainManager` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="a097a-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="a097a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a097a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a097a-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a097a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a097a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a097a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a097a-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a097a-116">The call timed out.</span></span>|  
|<span data-ttu-id="a097a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a097a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a097a-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a097a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a097a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a097a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a097a-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a097a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a097a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a097a-121">E_FAIL</span></span>|<span data-ttu-id="a097a-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a097a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a097a-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="a097a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a097a-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a097a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a097a-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a097a-125">Remarks</span></span>  
 <span data-ttu-id="a097a-126"><xref:System.AppDomainManager> zapewnia hosta z mechanizmem ładowania do kodu zarządzanego i kontrolowania tworzenia i ustawień poszczególnych <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a097a-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="a097a-127"><xref:System.AppDomainManager> jest ładowany do każdej <xref:System.AppDomain> po utworzeniu <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a097a-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="a097a-128">W przypadku wybrania tej opcji środowisko CLR powiadamia hosta o utworzeniu domeny aplikacji przez ustawienie wartości parametru `pUnkAppDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="a097a-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="a097a-129">W implementacji metody `SetAppDomainManager` host może ustawić nazwę zestawu i typ dla Menedżera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a097a-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a097a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a097a-130">Requirements</span></span>  
 <span data-ttu-id="a097a-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a097a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a097a-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a097a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a097a-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a097a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a097a-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a097a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a097a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a097a-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="a097a-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="a097a-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
