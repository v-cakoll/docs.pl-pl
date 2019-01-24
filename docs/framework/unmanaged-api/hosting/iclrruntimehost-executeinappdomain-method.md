---
title: ICLRRuntimeHost::ExecuteInAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5a1ae284b4f2474cb824ee9dbff2eb82c5a0ead
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568793"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="e6bb5-102">ICLRRuntimeHost::ExecuteInAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="e6bb5-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="e6bb5-103">Określa <xref:System.AppDomain> w którym można wykonać określonego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6bb5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6bb5-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6bb5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6bb5-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="e6bb5-106">[in] Identyfikator numeryczny <xref:System.AppDomain> w którym można wykonać określonej metody.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="e6bb5-107">[in] Wskaźnik do funkcji, które można wykonać w ramach określonych <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="e6bb5-108">[in] Wskaźnik do pamięci przydzielonej przez obiekt wywołujący nieprzezroczystości.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="e6bb5-109">Ten parametr jest przekazywany przez środowisko uruchomieniowe języka wspólnego (CLR) do wywołania zwrotnego domeny.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="e6bb5-110">Nie jest pamięci sterty zarządzanej w czasie wykonywania. alokacji i okresie istnienia tej pamięci są kontrolowane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6bb5-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e6bb5-111">Return Value</span></span>  
  
|<span data-ttu-id="e6bb5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6bb5-112">HRESULT</span></span>|<span data-ttu-id="e6bb5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e6bb5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6bb5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6bb5-114">S_OK</span></span>|<span data-ttu-id="e6bb5-115">`ExecuteInAppDomain` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="e6bb5-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6bb5-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6bb5-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e6bb5-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e6bb5-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e6bb5-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-119">The call timed out.</span></span>|  
|<span data-ttu-id="e6bb5-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6bb5-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e6bb5-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e6bb5-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e6bb5-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e6bb5-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e6bb5-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6bb5-124">E_FAIL</span></span>|<span data-ttu-id="e6bb5-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e6bb5-126">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e6bb5-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6bb5-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6bb5-128">Remarks</span></span>  
 <span data-ttu-id="e6bb5-129">`ExecuteInAppDomain` Zezwalaj hostowi sprawowania kontroli nad tym tryb failover, które zarządzane <xref:System.AppDomain> określonej metody zarządzanych powinna zostać wykonana w.</span><span class="sxs-lookup"><span data-stu-id="e6bb5-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="e6bb5-130">Można pobrać wartość identyfikatora domeny aplikacji, który odnosi się do wartości <xref:System.AppDomain.Id%2A> właściwość, wywołując [getcurrentappdomainid — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="e6bb5-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6bb5-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6bb5-131">Requirements</span></span>  
 <span data-ttu-id="e6bb5-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6bb5-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6bb5-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e6bb5-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6bb5-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6bb5-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6bb5-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6bb5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6bb5-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6bb5-136">See also</span></span>
- [<span data-ttu-id="e6bb5-137">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="e6bb5-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
