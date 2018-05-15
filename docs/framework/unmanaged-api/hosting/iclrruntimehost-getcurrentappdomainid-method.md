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
ms.openlocfilehash: cbe6ac3c9f03de2224f933a7e44325f578ded48b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="20662-102">ICLRRuntimeHost::GetCurrentAppDomainId — Metoda</span><span class="sxs-lookup"><span data-stu-id="20662-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="20662-103">Pobiera identyfikator numeryczny z <xref:System.AppDomain> który jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="20662-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20662-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20662-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20662-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20662-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="20662-106">[out] Identyfikator numeryczny z <xref:System.AppDomain> który jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="20662-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20662-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="20662-107">Return Value</span></span>  
  
|<span data-ttu-id="20662-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20662-108">HRESULT</span></span>|<span data-ttu-id="20662-109">Opis</span><span class="sxs-lookup"><span data-stu-id="20662-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20662-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="20662-110">S_OK</span></span>|<span data-ttu-id="20662-111">`GetCurrentAppDomainId` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="20662-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="20662-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20662-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20662-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="20662-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20662-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20662-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20662-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="20662-115">The call timed out.</span></span>|  
|<span data-ttu-id="20662-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20662-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20662-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="20662-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20662-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20662-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20662-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="20662-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20662-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20662-120">E_FAIL</span></span>|<span data-ttu-id="20662-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="20662-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20662-122">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="20662-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20662-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="20662-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20662-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20662-124">Remarks</span></span>  
 <span data-ttu-id="20662-125">`pdwAppDomainId` Parametr ma ustawioną wartość <xref:System.AppDomain.Id%2A> właściwość <xref:System.AppDomain> , w którym jest wykonywany bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="20662-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20662-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20662-126">Requirements</span></span>  
 <span data-ttu-id="20662-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20662-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20662-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20662-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20662-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20662-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20662-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20662-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20662-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20662-131">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="20662-132">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="20662-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
