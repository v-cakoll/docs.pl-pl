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
ms.openlocfilehash: c012e4e2b5e41737f7bbe6a0fb887693b0ba22c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176425"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="be35f-102">ICLRRuntimeHost::ExecuteInAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="be35f-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="be35f-103">Określa, <xref:System.AppDomain> w którym ma być wykonywany określony kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="be35f-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be35f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be35f-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be35f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be35f-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="be35f-106">[w] Identyfikator numeryczny, <xref:System.AppDomain> w którym należy wykonać określoną metodę.</span><span class="sxs-lookup"><span data-stu-id="be35f-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="be35f-107">[w] Wskaźnik do funkcji do wykonania <xref:System.AppDomain>w ramach określonego .</span><span class="sxs-lookup"><span data-stu-id="be35f-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="be35f-108">[w] Wskaźnik do nieprzezroczystej pamięci przydzielonej przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="be35f-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="be35f-109">Ten parametr jest przekazywany przez środowisko uruchomieniowe języka wspólnego (CLR) do wywołania zwrotnego domeny.</span><span class="sxs-lookup"><span data-stu-id="be35f-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="be35f-110">Nie jest pamięcią sterty zarządzanej przez środowisko uruchomieniowe; alokacji i okresu istnienia tej pamięci są kontrolowane przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="be35f-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be35f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="be35f-111">Return Value</span></span>  
  
|<span data-ttu-id="be35f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be35f-112">HRESULT</span></span>|<span data-ttu-id="be35f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="be35f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be35f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="be35f-114">S_OK</span></span>|<span data-ttu-id="be35f-115">`ExecuteInAppDomain`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="be35f-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="be35f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be35f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be35f-117">Clr nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="be35f-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="be35f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="be35f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="be35f-119">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="be35f-119">The call timed out.</span></span>|  
|<span data-ttu-id="be35f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="be35f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="be35f-121">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="be35f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="be35f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="be35f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="be35f-123">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="be35f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="be35f-124">E_fail</span><span class="sxs-lookup"><span data-stu-id="be35f-124">E_FAIL</span></span>|<span data-ttu-id="be35f-125">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="be35f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="be35f-126">Jeśli metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="be35f-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="be35f-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="be35f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be35f-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be35f-128">Remarks</span></span>  
 <span data-ttu-id="be35f-129">`ExecuteInAppDomain`umożliwia hostowi sprawowanie kontroli <xref:System.AppDomain> nad tym, w którym zarządzanej metody zarządzanej powinna być wykonywana.</span><span class="sxs-lookup"><span data-stu-id="be35f-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="be35f-130">Można uzyskać wartość identyfikatora domeny aplikacji, który odpowiada wartości <xref:System.AppDomain.Id%2A> właściwości, wywołując Metodę [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="be35f-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be35f-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be35f-131">Requirements</span></span>  
 <span data-ttu-id="be35f-132">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be35f-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be35f-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="be35f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be35f-134">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be35f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be35f-135">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be35f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be35f-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be35f-136">See also</span></span>

- [<span data-ttu-id="be35f-137">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="be35f-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
