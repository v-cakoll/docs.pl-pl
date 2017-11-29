---
title: "IHostSecurityContext::Capture — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityContext.Capture
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 100ce151b81fb240434b1072be8fe8c354f85440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="733aa-102">IHostSecurityContext::Capture — Metoda</span><span class="sxs-lookup"><span data-stu-id="733aa-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="733aa-103">Pobiera Sklonowanie [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) wystąpienia zwrócone w wyniku wywołania [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="733aa-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="733aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="733aa-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="733aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="733aa-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="733aa-106">[out] Wskaźnik do adresu Sklonowanie `IHostSecurityContext` obiektu do przechwycenia.</span><span class="sxs-lookup"><span data-stu-id="733aa-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="733aa-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="733aa-107">Return Value</span></span>  
  
|<span data-ttu-id="733aa-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="733aa-108">HRESULT</span></span>|<span data-ttu-id="733aa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="733aa-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="733aa-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="733aa-110">S_OK</span></span>|<span data-ttu-id="733aa-111">`Capture`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="733aa-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="733aa-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="733aa-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="733aa-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="733aa-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="733aa-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="733aa-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="733aa-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="733aa-115">The call timed out.</span></span>|  
|<span data-ttu-id="733aa-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="733aa-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="733aa-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="733aa-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="733aa-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="733aa-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="733aa-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="733aa-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="733aa-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="733aa-120">E_FAIL</span></span>|<span data-ttu-id="733aa-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="733aa-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="733aa-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="733aa-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="733aa-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="733aa-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="733aa-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="733aa-124">Remarks</span></span>  
 <span data-ttu-id="733aa-125">Wskaźnik interfejsu zwrócony z `Capture` jest Sklonowanie przechwyconych kontekstu.</span><span class="sxs-lookup"><span data-stu-id="733aa-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="733aa-126">Gdy te informacje są przenoszone przez punkt kodu asynchroniczne, jego okres istnienia jest oddzielony od elementu wskaźnika, względem którego wykonano wywołanie.</span><span class="sxs-lookup"><span data-stu-id="733aa-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="733aa-127">W związku z tym może być zwolnione oryginalnego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="733aa-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="733aa-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="733aa-128">Requirements</span></span>  
 <span data-ttu-id="733aa-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="733aa-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="733aa-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="733aa-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="733aa-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="733aa-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="733aa-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="733aa-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733aa-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="733aa-133">See Also</span></span>  
 [<span data-ttu-id="733aa-134">IHostSecurityContext — interfejs</span><span class="sxs-lookup"><span data-stu-id="733aa-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="733aa-135">IHostSecurityManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="733aa-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
