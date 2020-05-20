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
ms.openlocfilehash: 293c1764f4c0d857138726b8ed4855b1e3b03116
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703919"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="3b35f-102">ICLRRuntimeHost::UnloadAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b35f-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="3b35f-103">Zwalnia zarządzane <xref:System.AppDomain> odnoszące się do określonego identyfikatora liczbowego.</span><span class="sxs-lookup"><span data-stu-id="3b35f-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b35f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b35f-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b35f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b35f-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="3b35f-106">podczas Liczbowy identyfikator domeny aplikacji do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="3b35f-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="3b35f-107">[w] `true` Aby wskazać, że środowisko uruchomieniowe języka wspólnego (CLR) musi czekać, aż zakończy wykonywanie bieżącego wątku aplikacji przed podjęciem próby zwolnienia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b35f-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b35f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3b35f-108">Return Value</span></span>  
  
|<span data-ttu-id="3b35f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b35f-109">HRESULT</span></span>|<span data-ttu-id="3b35f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3b35f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b35f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b35f-111">S_OK</span></span>|<span data-ttu-id="3b35f-112">`UnloadAppDomain`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="3b35f-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="3b35f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3b35f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3b35f-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3b35f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3b35f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3b35f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3b35f-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="3b35f-116">The call timed out.</span></span>|  
|<span data-ttu-id="3b35f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3b35f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3b35f-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="3b35f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3b35f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3b35f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3b35f-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="3b35f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3b35f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3b35f-121">E_FAIL</span></span>|<span data-ttu-id="3b35f-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3b35f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3b35f-123">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="3b35f-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3b35f-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3b35f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b35f-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b35f-125">Remarks</span></span>  
 <span data-ttu-id="3b35f-126">Można uzyskać identyfikator liczbowy domeny aplikacji, w której jest wykonywany bieżący wątek przez wywołanie [GetCurrentAppDomainId —](iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="3b35f-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="3b35f-127">Ten identyfikator odpowiada <xref:System.AppDomain.Id%2A> właściwości <xref:System.AppDomain> typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3b35f-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b35f-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b35f-128">Requirements</span></span>  
 <span data-ttu-id="3b35f-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b35f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b35f-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3b35f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b35f-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3b35f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b35f-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b35f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b35f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b35f-133">See also</span></span>

- [<span data-ttu-id="3b35f-134">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b35f-134">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
