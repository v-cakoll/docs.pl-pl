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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f262c416a6998ed182d0c42d7f00ea7dcb3f898
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768677"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="1792e-102">ICLRRuntimeHost::GetCurrentAppDomainId — Metoda</span><span class="sxs-lookup"><span data-stu-id="1792e-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="1792e-103">Pobiera identyfikator liczbowy z <xref:System.AppDomain> obecnie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="1792e-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1792e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1792e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1792e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1792e-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="1792e-106">[out] Identyfikator numeryczny z <xref:System.AppDomain> obecnie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="1792e-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1792e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1792e-107">Return Value</span></span>  
  
|<span data-ttu-id="1792e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1792e-108">HRESULT</span></span>|<span data-ttu-id="1792e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1792e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1792e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1792e-110">S_OK</span></span>|<span data-ttu-id="1792e-111">`GetCurrentAppDomainId` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="1792e-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="1792e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1792e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1792e-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1792e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1792e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1792e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1792e-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1792e-115">The call timed out.</span></span>|  
|<span data-ttu-id="1792e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1792e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1792e-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="1792e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1792e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1792e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1792e-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1792e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1792e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1792e-120">E_FAIL</span></span>|<span data-ttu-id="1792e-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1792e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1792e-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1792e-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1792e-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1792e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1792e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1792e-124">Remarks</span></span>  
 <span data-ttu-id="1792e-125">`pdwAppDomainId` Parametr jest ustawiony na wartość <xref:System.AppDomain.Id%2A> właściwość <xref:System.AppDomain> w jest wykonywanie bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="1792e-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1792e-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1792e-126">Requirements</span></span>  
 <span data-ttu-id="1792e-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1792e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1792e-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1792e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1792e-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1792e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1792e-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1792e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1792e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1792e-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="1792e-132">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1792e-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
