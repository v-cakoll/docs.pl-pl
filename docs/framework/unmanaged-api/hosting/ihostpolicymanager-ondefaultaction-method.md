---
title: IHostPolicyManager::OnDefaultAction — Metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17a14b09de14f32e2ae3646f7847d44307ab3b53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439065"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="eb2f3-102">IHostPolicyManager::OnDefaultAction — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb2f3-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="eb2f3-103">Powiadamia hosta, którego środowisko uruchomieniowe języka wspólnego (CLR) ma mieć domyślnej akcji, który został ustawiony przez wywołanie do [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) metody w odpowiedzi na przerwanie wątku lub <xref:System.AppDomain> zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb2f3-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb2f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb2f3-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="eb2f3-106">[in] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości i wskazujący rodzaj zdarzenia, któremu odpowiada środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="eb2f3-107">[in] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości i wskazujący akcję, która podejmuje CLR w odpowiedzi na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb2f3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eb2f3-108">Return Value</span></span>  
  
|<span data-ttu-id="eb2f3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eb2f3-109">HRESULT</span></span>|<span data-ttu-id="eb2f3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="eb2f3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb2f3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb2f3-111">S_OK</span></span>|<span data-ttu-id="eb2f3-112">`OnDefaultAction` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="eb2f3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eb2f3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eb2f3-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub przetwarzania wywołania.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="eb2f3-115">pomyślnie</span><span class="sxs-lookup"><span data-stu-id="eb2f3-115">successfully</span></span>|  
|<span data-ttu-id="eb2f3-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eb2f3-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eb2f3-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-117">The call timed out.</span></span>|  
|<span data-ttu-id="eb2f3-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eb2f3-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eb2f3-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eb2f3-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eb2f3-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eb2f3-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eb2f3-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eb2f3-122">E_FAIL</span></span>|<span data-ttu-id="eb2f3-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eb2f3-124">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eb2f3-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eb2f3-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb2f3-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb2f3-126">Requirements</span></span>  
 <span data-ttu-id="eb2f3-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb2f3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2f3-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eb2f3-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb2f3-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb2f3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb2f3-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2f3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2f3-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb2f3-131">See Also</span></span>  
 [<span data-ttu-id="eb2f3-132">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eb2f3-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="eb2f3-133">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eb2f3-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="eb2f3-134">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb2f3-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="eb2f3-135">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb2f3-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
