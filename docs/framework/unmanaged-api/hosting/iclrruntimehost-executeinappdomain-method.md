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
ms.openlocfilehash: c847f177f48d72f28192d1efabe93c65a7b3f4b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120491"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="bf36a-102">ICLRRuntimeHost::ExecuteInAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf36a-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="bf36a-103">Określa <xref:System.AppDomain>, w którym ma zostać wykonany określony kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="bf36a-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf36a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf36a-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf36a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf36a-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="bf36a-106">podczas Identyfikator liczbowy <xref:System.AppDomain>, w którym ma zostać wykonana określona metoda.</span><span class="sxs-lookup"><span data-stu-id="bf36a-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="bf36a-107">podczas Wskaźnik do funkcji, która ma zostać wykonana w obrębie określonego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="bf36a-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="bf36a-108">podczas Wskaźnik do nieprzezroczystej pamięci przydzielonyj przez proces wywołujący.</span><span class="sxs-lookup"><span data-stu-id="bf36a-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="bf36a-109">Ten parametr jest przesyłany przez środowisko uruchomieniowe języka wspólnego (CLR) do wywołania zwrotnego domeny.</span><span class="sxs-lookup"><span data-stu-id="bf36a-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="bf36a-110">Nie jest to pamięć sterty zarządzana przez środowisko uruchomieniowe; Alokacja i okres istnienia tej pamięci są kontrolowane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="bf36a-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf36a-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bf36a-111">Return Value</span></span>  
  
|<span data-ttu-id="bf36a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf36a-112">HRESULT</span></span>|<span data-ttu-id="bf36a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bf36a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf36a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf36a-114">S_OK</span></span>|<span data-ttu-id="bf36a-115">`ExecuteInAppDomain` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="bf36a-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="bf36a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bf36a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bf36a-117">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bf36a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bf36a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bf36a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bf36a-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="bf36a-119">The call timed out.</span></span>|  
|<span data-ttu-id="bf36a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bf36a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bf36a-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="bf36a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bf36a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bf36a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bf36a-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="bf36a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bf36a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf36a-124">E_FAIL</span></span>|<span data-ttu-id="bf36a-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bf36a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bf36a-126">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="bf36a-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bf36a-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bf36a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf36a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf36a-128">Remarks</span></span>  
 <span data-ttu-id="bf36a-129">`ExecuteInAppDomain` umożliwia hostowi wykonywanie kontroli nad tym, które zarządzane <xref:System.AppDomain> należy wykonać określoną metodę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="bf36a-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="bf36a-130">Możesz uzyskać wartość identyfikatora domeny aplikacji, która odpowiada wartości właściwości <xref:System.AppDomain.Id%2A>, wywołując [metodę GetCurrentAppDomainId —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="bf36a-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf36a-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf36a-131">Requirements</span></span>  
 <span data-ttu-id="bf36a-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf36a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf36a-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bf36a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf36a-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bf36a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf36a-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf36a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf36a-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf36a-136">See also</span></span>

- [<span data-ttu-id="bf36a-137">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf36a-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
