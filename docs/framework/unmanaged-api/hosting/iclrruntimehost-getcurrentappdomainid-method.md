---
title: "ICLRRuntimeHost::GetCurrentAppDomainId — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.GetCurrentAppDomainId
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 001a467536c899c3849b5689e65bdaf404beab75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="36086-102">ICLRRuntimeHost::GetCurrentAppDomainId — Metoda</span><span class="sxs-lookup"><span data-stu-id="36086-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="36086-103">Pobiera identyfikator numeryczny z <xref:System.AppDomain> który jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="36086-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36086-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36086-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36086-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36086-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="36086-106">[out] Identyfikator numeryczny z <xref:System.AppDomain> który jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="36086-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36086-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="36086-107">Return Value</span></span>  
  
|<span data-ttu-id="36086-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36086-108">HRESULT</span></span>|<span data-ttu-id="36086-109">Opis</span><span class="sxs-lookup"><span data-stu-id="36086-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36086-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="36086-110">S_OK</span></span>|<span data-ttu-id="36086-111">`GetCurrentAppDomainId`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="36086-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="36086-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36086-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36086-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="36086-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="36086-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="36086-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="36086-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="36086-115">The call timed out.</span></span>|  
|<span data-ttu-id="36086-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="36086-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="36086-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="36086-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="36086-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="36086-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="36086-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="36086-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="36086-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="36086-120">E_FAIL</span></span>|<span data-ttu-id="36086-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="36086-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="36086-122">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="36086-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="36086-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="36086-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36086-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36086-124">Remarks</span></span>  
 <span data-ttu-id="36086-125">`pdwAppDomainId` Parametr ma ustawioną wartość <xref:System.AppDomain.Id%2A> właściwość <xref:System.AppDomain> , w którym jest wykonywany bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="36086-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36086-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36086-126">Requirements</span></span>  
 <span data-ttu-id="36086-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36086-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36086-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36086-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36086-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36086-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36086-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36086-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36086-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36086-131">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="36086-132">ICLRRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="36086-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
