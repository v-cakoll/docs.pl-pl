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
ms.openlocfilehash: 6194478922bb1634f8a96de420fb17af10666322
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560961"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="6cbb1-102">ICLRRuntimeHost::UnloadAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="6cbb1-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="6cbb1-103">Zwalnia zarządzanej <xref:System.AppDomain> , który odpowiada określony identyfikator liczbowy.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cbb1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6cbb1-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cbb1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cbb1-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="6cbb1-106">[in] Identyfikator liczbowy domeny aplikacji, aby zwolnić.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="6cbb1-107">[in] `true` do wskazania, że środowisko uruchomieniowe języka wspólnego (CLR) muszą czekać, aż zakończy się wykonywanie bieżącego wątku aplikacji przed podjęciem próby zwolnienie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cbb1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6cbb1-108">Return Value</span></span>  
  
|<span data-ttu-id="6cbb1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cbb1-109">HRESULT</span></span>|<span data-ttu-id="6cbb1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6cbb1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6cbb1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6cbb1-111">S_OK</span></span>|<span data-ttu-id="6cbb1-112">`UnloadAppDomain` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="6cbb1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6cbb1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6cbb1-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6cbb1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6cbb1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6cbb1-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-116">The call timed out.</span></span>|  
|<span data-ttu-id="6cbb1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6cbb1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6cbb1-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6cbb1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6cbb1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6cbb1-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6cbb1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6cbb1-121">E_FAIL</span></span>|<span data-ttu-id="6cbb1-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6cbb1-123">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6cbb1-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cbb1-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cbb1-125">Remarks</span></span>  
 <span data-ttu-id="6cbb1-126">Możesz uzyskać identyfikator liczbowy domeny aplikacji, w którym bieżącego wątku jest wykonywana przez wywołanie metody [getcurrentappdomainid —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="6cbb1-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="6cbb1-127">Ten identyfikator odnosi się do <xref:System.AppDomain.Id%2A> właściwość zarządzaną <xref:System.AppDomain> typu.</span><span class="sxs-lookup"><span data-stu-id="6cbb1-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cbb1-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6cbb1-128">Requirements</span></span>  
 <span data-ttu-id="6cbb1-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cbb1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cbb1-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cbb1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cbb1-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cbb1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cbb1-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cbb1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbb1-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cbb1-133">See also</span></span>
- [<span data-ttu-id="6cbb1-134">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cbb1-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
