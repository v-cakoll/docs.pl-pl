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
ms.openlocfilehash: 9f988084310b920907bb7f212e7d40ca0d1c91db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197519"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="71d41-102">ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="71d41-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="71d41-103">Określa zachowanie środowiska uruchomieniowego języka wspólnego (CLR), po wystąpieniu nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="71d41-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d41-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71d41-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71d41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71d41-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="71d41-106">[in] Jedną z [eclrunhandledexception —](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) wartości, wskazującą, czy zachowanie jest ustawiony przez środowisko CLR lub hosta.</span><span class="sxs-lookup"><span data-stu-id="71d41-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71d41-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="71d41-107">Return Value</span></span>  
  
|<span data-ttu-id="71d41-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71d41-108">HRESULT</span></span>|<span data-ttu-id="71d41-109">Opis</span><span class="sxs-lookup"><span data-stu-id="71d41-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71d41-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="71d41-110">S_OK</span></span>|`SetUnhandledExceptionPolicy` <span data-ttu-id="71d41-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="71d41-111">returned successfully.</span></span>|  
|<span data-ttu-id="71d41-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71d41-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71d41-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="71d41-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71d41-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71d41-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71d41-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="71d41-115">The call timed out.</span></span>|  
|<span data-ttu-id="71d41-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71d41-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71d41-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="71d41-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71d41-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71d41-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71d41-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="71d41-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71d41-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71d41-120">E_FAIL</span></span>|<span data-ttu-id="71d41-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="71d41-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71d41-122">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="71d41-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71d41-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="71d41-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71d41-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71d41-124">Remarks</span></span>  
 <span data-ttu-id="71d41-125">Domyślnie środowisko CLR jest ostatnim Obsługa wszystkie nieobsłużone wyjątki, a jej zachowanie domyślne jest zrywać proces.</span><span class="sxs-lookup"><span data-stu-id="71d41-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="71d41-126">Hosta można zmienić to zachowanie przez ustawienie `policy` wartość eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="71d41-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="71d41-127">Ta wartość umożliwia hosta zaimplementować własną zachowanie domyślne, podobnie jak w przypadku wcześniejszych wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="71d41-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d41-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71d41-128">Requirements</span></span>  
 <span data-ttu-id="71d41-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71d41-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71d41-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71d41-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71d41-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="71d41-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="71d41-132">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="71d41-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71d41-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71d41-133">See also</span></span>

- [<span data-ttu-id="71d41-134">EClrUnhandledException — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="71d41-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="71d41-135">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="71d41-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="71d41-136">ICLRPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="71d41-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="71d41-137">IHostPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="71d41-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
