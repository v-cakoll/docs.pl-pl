---
title: "ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 59ff5cfd93d8077388694ee2e155133a88319c47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="4ac34-102">ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="4ac34-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="4ac34-103">Określa zachowanie środowisko uruchomieniowe języka wspólnego (CLR), gdy wystąpi nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4ac34-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac34-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ac34-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ac34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ac34-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="4ac34-106">[in] Jeden z [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) wartości, wskazującą, czy zachowanie jest ustawiony przez środowisko CLR lub hosta.</span><span class="sxs-lookup"><span data-stu-id="4ac34-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ac34-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4ac34-107">Return Value</span></span>  
  
|<span data-ttu-id="4ac34-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ac34-108">HRESULT</span></span>|<span data-ttu-id="4ac34-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4ac34-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ac34-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ac34-110">S_OK</span></span>|<span data-ttu-id="4ac34-111">`SetUnhandledExceptionPolicy`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4ac34-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="4ac34-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4ac34-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4ac34-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="4ac34-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4ac34-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4ac34-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4ac34-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="4ac34-115">The call timed out.</span></span>|  
|<span data-ttu-id="4ac34-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4ac34-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4ac34-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="4ac34-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4ac34-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4ac34-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4ac34-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="4ac34-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4ac34-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4ac34-120">E_FAIL</span></span>|<span data-ttu-id="4ac34-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4ac34-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4ac34-122">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="4ac34-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4ac34-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4ac34-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ac34-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ac34-124">Remarks</span></span>  
 <span data-ttu-id="4ac34-125">Domyślnie środowisko CLR jest końcowa procedura obsługi dla wszystkich nieobsługiwanych wyjątków, a jego domyślnym zachowaniem jest zerwanie procesu.</span><span class="sxs-lookup"><span data-stu-id="4ac34-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="4ac34-126">Hosta można zmienić to zachowanie, ustawiając `policy` wartość eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="4ac34-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="4ac34-127">Ta wartość umożliwia hosta do zaimplementowania własną zachowanie domyślne, tak jak w przypadku wcześniejszych wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="4ac34-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ac34-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ac34-128">Requirements</span></span>  
 <span data-ttu-id="4ac34-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ac34-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ac34-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4ac34-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ac34-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ac34-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ac34-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ac34-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac34-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ac34-133">See Also</span></span>  
 [<span data-ttu-id="4ac34-134">EClrUnhandledException — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4ac34-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 [<span data-ttu-id="4ac34-135">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="4ac34-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="4ac34-136">ICLRPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="4ac34-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="4ac34-137">IHostPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="4ac34-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
