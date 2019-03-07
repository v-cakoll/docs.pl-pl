---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 734bd51131ea922f00362e7306d34e5241231c13
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466844"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="5ee3f-102">ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="5ee3f-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="5ee3f-103">Określa zachowanie środowiska uruchomieniowego języka wspólnego (CLR), po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ee3f-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ee3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ee3f-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="5ee3f-106">[in] Jedną z [eclrunhandledexception —](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) wartości, wskazującą, czy zachowanie jest ustawiony przez środowisko CLR lub hosta.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ee3f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5ee3f-107">Return Value</span></span>  
  
|<span data-ttu-id="5ee3f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ee3f-108">HRESULT</span></span>|<span data-ttu-id="5ee3f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5ee3f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ee3f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ee3f-110">S_OK</span></span>|<span data-ttu-id="5ee3f-111">`SetUnhandledExceptionPolicy` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="5ee3f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5ee3f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5ee3f-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5ee3f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5ee3f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5ee3f-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-115">The call timed out.</span></span>|  
|<span data-ttu-id="5ee3f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5ee3f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5ee3f-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5ee3f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5ee3f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5ee3f-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5ee3f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5ee3f-120">E_FAIL</span></span>|<span data-ttu-id="5ee3f-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5ee3f-122">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5ee3f-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ee3f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ee3f-124">Remarks</span></span>  
 <span data-ttu-id="5ee3f-125">Domyślnie środowisko CLR jest ostatnim Obsługa wszystkie nieobsłużone wyjątki, a jej zachowanie domyślne jest zrywać proces.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="5ee3f-126">Hosta można zmienić to zachowanie przez ustawienie `policy` wartość eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="5ee3f-127">Ta wartość umożliwia hosta zaimplementować własną zachowanie domyślne, podobnie jak w przypadku wcześniejszych wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5ee3f-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee3f-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ee3f-128">Requirements</span></span>  
 <span data-ttu-id="5ee3f-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ee3f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ee3f-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5ee3f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ee3f-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5ee3f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ee3f-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ee3f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee3f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ee3f-133">See also</span></span>
- [<span data-ttu-id="5ee3f-134">EClrUnhandledException, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5ee3f-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="5ee3f-135">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ee3f-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="5ee3f-136">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ee3f-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="5ee3f-137">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ee3f-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
