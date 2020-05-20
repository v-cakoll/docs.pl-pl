---
title: ICLRRuntimeHost::GetCurrentAppDomainId — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
ms.openlocfilehash: 1c667b19ac4bfa0bea95b85cf099906e351e5b71
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703670"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="e775e-102">ICLRRuntimeHost::GetCurrentAppDomainId — Metoda</span><span class="sxs-lookup"><span data-stu-id="e775e-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="e775e-103">Pobiera liczbowy identyfikator <xref:System.AppDomain> , który jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="e775e-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e775e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e775e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e775e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e775e-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="e775e-106">określoną Liczbowy identyfikator <xref:System.AppDomain> , który jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="e775e-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e775e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e775e-107">Return Value</span></span>  
  
|<span data-ttu-id="e775e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e775e-108">HRESULT</span></span>|<span data-ttu-id="e775e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e775e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e775e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e775e-110">S_OK</span></span>|<span data-ttu-id="e775e-111">`GetCurrentAppDomainId`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="e775e-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="e775e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e775e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e775e-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e775e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e775e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e775e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e775e-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e775e-115">The call timed out.</span></span>|  
|<span data-ttu-id="e775e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e775e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e775e-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e775e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e775e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e775e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e775e-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="e775e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e775e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e775e-120">E_FAIL</span></span>|<span data-ttu-id="e775e-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e775e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e775e-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="e775e-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e775e-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e775e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e775e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e775e-124">Remarks</span></span>  
 <span data-ttu-id="e775e-125">`pdwAppDomainId`Parametr jest ustawiony na wartość <xref:System.AppDomain.Id%2A> właściwości, <xref:System.AppDomain> w której jest wykonywany bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="e775e-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e775e-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e775e-126">Requirements</span></span>  
 <span data-ttu-id="e775e-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e775e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e775e-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e775e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e775e-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e775e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e775e-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e775e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e775e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e775e-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="e775e-132">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="e775e-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
