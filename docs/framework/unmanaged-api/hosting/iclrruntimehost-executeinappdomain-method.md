---
title: "ICLRRuntimeHost::ExecuteInAppDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8c540c9618655e6df30ad253e0c4cccdf6624e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="aa6e0-102">ICLRRuntimeHost::ExecuteInAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa6e0-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="aa6e0-103">Określa <xref:System.AppDomain> polegający na wykonanie określonego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa6e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa6e0-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa6e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa6e0-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="aa6e0-106">[in] Numeryczny identyfikator <xref:System.AppDomain> w którym można wykonać określonej metody.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="aa6e0-107">[in] Wskaźnik do funkcji, które można wykonać w ramach określonego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="aa6e0-108">[in] Wskaźnik do nieprzezroczyste pamięci przydzielone przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="aa6e0-109">Ten parametr jest przekazywany przez środowisko uruchomieniowe języka wspólnego (CLR) do domeny wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="aa6e0-110">Nie jest pamięci sterty zarządzanego środowiska wykonawczego. alokacji i okres istnienia tej pamięci są kontrolowane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa6e0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa6e0-111">Return Value</span></span>  
  
|<span data-ttu-id="aa6e0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa6e0-112">HRESULT</span></span>|<span data-ttu-id="aa6e0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="aa6e0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa6e0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa6e0-114">S_OK</span></span>|<span data-ttu-id="aa6e0-115">`ExecuteInAppDomain`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="aa6e0-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa6e0-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa6e0-117">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa6e0-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa6e0-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa6e0-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-119">The call timed out.</span></span>|  
|<span data-ttu-id="aa6e0-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa6e0-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa6e0-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa6e0-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa6e0-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa6e0-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa6e0-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa6e0-124">E_FAIL</span></span>|<span data-ttu-id="aa6e0-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa6e0-126">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa6e0-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa6e0-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa6e0-128">Remarks</span></span>  
 <span data-ttu-id="aa6e0-129">`ExecuteInAppDomain`Umożliwia hosta sprawowanie kontroli over zarządzanych <xref:System.AppDomain> określonej metody zarządzane mają zostać wykonane w.</span><span class="sxs-lookup"><span data-stu-id="aa6e0-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="aa6e0-130">Można pobrać wartości identyfikatora domeny aplikacji, co odpowiada wartości <xref:System.AppDomain.Id%2A> właściwości, wywołując [GetCurrentAppDomainId — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="aa6e0-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa6e0-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa6e0-131">Requirements</span></span>  
 <span data-ttu-id="aa6e0-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa6e0-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa6e0-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa6e0-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa6e0-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa6e0-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa6e0-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa6e0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa6e0-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa6e0-136">See Also</span></span>  
 [<span data-ttu-id="aa6e0-137">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa6e0-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
