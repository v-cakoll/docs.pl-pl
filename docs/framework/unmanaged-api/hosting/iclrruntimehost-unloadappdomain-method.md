---
title: ICLRRuntimeHost::UnloadAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e1a2358590b95b39b6495b74078f079c5b34876
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765677"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="50103-102">ICLRRuntimeHost::UnloadAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="50103-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="50103-103">Zwalnia zarządzanej <xref:System.AppDomain> , który odpowiada określony identyfikator liczbowy.</span><span class="sxs-lookup"><span data-stu-id="50103-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50103-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50103-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50103-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50103-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="50103-106">[in] Identyfikator liczbowy domeny aplikacji, aby zwolnić.</span><span class="sxs-lookup"><span data-stu-id="50103-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="50103-107">[in] `true` do wskazania, że środowisko uruchomieniowe języka wspólnego (CLR) muszą czekać, aż zakończy się wykonywanie bieżącego wątku aplikacji przed podjęciem próby zwolnienie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50103-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50103-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50103-108">Return Value</span></span>  
  
|<span data-ttu-id="50103-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50103-109">HRESULT</span></span>|<span data-ttu-id="50103-110">Opis</span><span class="sxs-lookup"><span data-stu-id="50103-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50103-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="50103-111">S_OK</span></span>|<span data-ttu-id="50103-112">`UnloadAppDomain` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="50103-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="50103-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50103-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50103-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="50103-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50103-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50103-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50103-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="50103-116">The call timed out.</span></span>|  
|<span data-ttu-id="50103-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50103-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50103-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="50103-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50103-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50103-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50103-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="50103-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50103-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50103-121">E_FAIL</span></span>|<span data-ttu-id="50103-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="50103-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50103-123">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="50103-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50103-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="50103-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50103-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50103-125">Remarks</span></span>  
 <span data-ttu-id="50103-126">Możesz uzyskać identyfikator liczbowy domeny aplikacji, w którym bieżącego wątku jest wykonywana przez wywołanie metody [getcurrentappdomainid —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="50103-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="50103-127">Ten identyfikator odnosi się do <xref:System.AppDomain.Id%2A> właściwość zarządzaną <xref:System.AppDomain> typu.</span><span class="sxs-lookup"><span data-stu-id="50103-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50103-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50103-128">Requirements</span></span>  
 <span data-ttu-id="50103-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50103-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50103-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50103-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50103-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50103-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50103-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50103-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50103-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50103-133">See also</span></span>

- [<span data-ttu-id="50103-134">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="50103-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
