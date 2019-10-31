---
title: ICLRControl::SetAppDomainManagerType — Metoda
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
ms.openlocfilehash: be29a4f83901b8e8fc338c2daa8f5703523402b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126587"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="fc814-102">ICLRControl::SetAppDomainManagerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc814-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="fc814-103">Ustawia typ pochodzący od <xref:System.AppDomainManager> jako typ dla menedżerów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fc814-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc814-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc814-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc814-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc814-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="fc814-106">podczas Nazwa zestawu, w którym zaimplementowano żądany typ pochodny od <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="fc814-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="fc814-107">podczas Nazwa typu zaimplementowanego w `pwzAppDomainManagerAssembly` parametr, który implementuje możliwości <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="fc814-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc814-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc814-108">Return Value</span></span>  
  
|<span data-ttu-id="fc814-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc814-109">HRESULT</span></span>|<span data-ttu-id="fc814-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fc814-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc814-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc814-111">S_OK</span></span>|<span data-ttu-id="fc814-112">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="fc814-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="fc814-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc814-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc814-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fc814-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc814-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc814-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc814-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="fc814-116">The call timed out.</span></span>|  
|<span data-ttu-id="fc814-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc814-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc814-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="fc814-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc814-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc814-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc814-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="fc814-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc814-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc814-121">E_FAIL</span></span>|<span data-ttu-id="fc814-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fc814-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc814-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="fc814-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc814-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc814-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc814-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc814-125">Requirements</span></span>  
 <span data-ttu-id="fc814-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc814-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc814-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fc814-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc814-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc814-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc814-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc814-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc814-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc814-130">See also</span></span>

- [<span data-ttu-id="fc814-131">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc814-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="fc814-132">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc814-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
