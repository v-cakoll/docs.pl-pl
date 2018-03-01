---
title: "ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ad287fedbc06768dd683c254292e0c28760d59a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="20cd1-102">ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="20cd1-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="20cd1-103">Określa zachowanie środowisko uruchomieniowe języka wspólnego (CLR), gdy wystąpi nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="20cd1-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20cd1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20cd1-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20cd1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20cd1-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="20cd1-106">[in] Jeden z [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) wartości, wskazującą, czy zachowanie jest ustawiony przez środowisko CLR lub hosta.</span><span class="sxs-lookup"><span data-stu-id="20cd1-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20cd1-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="20cd1-107">Return Value</span></span>  
  
|<span data-ttu-id="20cd1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20cd1-108">HRESULT</span></span>|<span data-ttu-id="20cd1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="20cd1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20cd1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="20cd1-110">S_OK</span></span>|<span data-ttu-id="20cd1-111">`SetUnhandledExceptionPolicy`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="20cd1-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="20cd1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20cd1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20cd1-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="20cd1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20cd1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20cd1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20cd1-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="20cd1-115">The call timed out.</span></span>|  
|<span data-ttu-id="20cd1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20cd1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20cd1-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="20cd1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20cd1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20cd1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20cd1-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="20cd1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20cd1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20cd1-120">E_FAIL</span></span>|<span data-ttu-id="20cd1-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="20cd1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20cd1-122">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="20cd1-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20cd1-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="20cd1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20cd1-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20cd1-124">Remarks</span></span>  
 <span data-ttu-id="20cd1-125">Domyślnie środowisko CLR jest końcowa procedura obsługi dla wszystkich nieobsługiwanych wyjątków, a jego domyślnym zachowaniem jest zerwanie procesu.</span><span class="sxs-lookup"><span data-stu-id="20cd1-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="20cd1-126">Hosta można zmienić to zachowanie, ustawiając `policy` wartość eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="20cd1-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="20cd1-127">Ta wartość umożliwia hosta do zaimplementowania własną zachowanie domyślne, tak jak w przypadku wcześniejszych wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="20cd1-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20cd1-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20cd1-128">Requirements</span></span>  
 <span data-ttu-id="20cd1-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20cd1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20cd1-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20cd1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20cd1-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20cd1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20cd1-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20cd1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20cd1-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20cd1-133">See Also</span></span>  
 [<span data-ttu-id="20cd1-134">EClrUnhandledException, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="20cd1-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 [<span data-ttu-id="20cd1-135">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="20cd1-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="20cd1-136">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="20cd1-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="20cd1-137">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="20cd1-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
