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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf20831b80df07f2861e3bab3b421b375d4774e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773208"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="d59a3-102">ICLRControl::SetAppDomainManagerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="d59a3-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="d59a3-103">Ustawia typ pochodzący od <xref:System.AppDomainManager> jako typ dla menedżerów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d59a3-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d59a3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d59a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d59a3-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="d59a3-106">[in] Nazwa zestawu, w którym żądanego typu pochodną <xref:System.AppDomainManager> jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="d59a3-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="d59a3-107">[in] Nazwa typu zaimplementowane w `pwzAppDomainManagerAssembly` parametr, który implementuje możliwości <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="d59a3-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d59a3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d59a3-108">Return Value</span></span>  
  
|<span data-ttu-id="d59a3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d59a3-109">HRESULT</span></span>|<span data-ttu-id="d59a3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d59a3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d59a3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d59a3-111">S_OK</span></span>|<span data-ttu-id="d59a3-112">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d59a3-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="d59a3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d59a3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d59a3-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d59a3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d59a3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d59a3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d59a3-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d59a3-116">The call timed out.</span></span>|  
|<span data-ttu-id="d59a3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d59a3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d59a3-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d59a3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d59a3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d59a3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d59a3-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d59a3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d59a3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d59a3-121">E_FAIL</span></span>|<span data-ttu-id="d59a3-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d59a3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d59a3-123">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d59a3-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d59a3-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d59a3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d59a3-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d59a3-125">Requirements</span></span>  
 <span data-ttu-id="d59a3-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d59a3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59a3-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d59a3-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d59a3-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d59a3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d59a3-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59a3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59a3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d59a3-130">See also</span></span>

- [<span data-ttu-id="d59a3-131">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="d59a3-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="d59a3-132">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="d59a3-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
