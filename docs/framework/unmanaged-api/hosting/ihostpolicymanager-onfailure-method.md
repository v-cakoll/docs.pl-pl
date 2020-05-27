---
title: IHostPolicyManager::OnFailure — Metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
ms.openlocfilehash: 8ad4943aa9bf1b66b34bcd83a5422a977b16518d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804229"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="eaa0f-102">IHostPolicyManager::OnFailure — Metoda</span><span class="sxs-lookup"><span data-stu-id="eaa0f-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="eaa0f-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma wykonać akcję określoną przez wywołanie metody [ICLRPolicyManager:: SetActionOnFailure —](iclrpolicymanager-setactiononfailure-method.md) w odpowiedzi na błąd alokacji zasobów lub operacji odzyskiwania.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eaa0f-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaa0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eaa0f-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="eaa0f-106">podczas Jedno z wartości [EClrFailure —](eclrfailure-enumeration.md) , wskazujące rodzaj niepowodzenia, do którego odpowiada środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="eaa0f-107">podczas Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) , wskazująca na akcję, do której trwa wykonywanie środowiska CLR `failure` .</span><span class="sxs-lookup"><span data-stu-id="eaa0f-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaa0f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eaa0f-108">Return Value</span></span>  
  
|<span data-ttu-id="eaa0f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eaa0f-109">HRESULT</span></span>|<span data-ttu-id="eaa0f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="eaa0f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eaa0f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eaa0f-111">S_OK</span></span>|<span data-ttu-id="eaa0f-112">`OnFailure`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="eaa0f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eaa0f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eaa0f-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eaa0f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eaa0f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eaa0f-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-116">The call timed out.</span></span>|  
|<span data-ttu-id="eaa0f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eaa0f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eaa0f-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eaa0f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eaa0f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eaa0f-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eaa0f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eaa0f-121">E_FAIL</span></span>|<span data-ttu-id="eaa0f-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eaa0f-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eaa0f-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eaa0f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eaa0f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eaa0f-125">Requirements</span></span>  
 <span data-ttu-id="eaa0f-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaa0f-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaa0f-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eaa0f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eaa0f-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eaa0f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eaa0f-129">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaa0f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa0f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eaa0f-130">See also</span></span>

- [<span data-ttu-id="eaa0f-131">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eaa0f-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="eaa0f-132">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eaa0f-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="eaa0f-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="eaa0f-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="eaa0f-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="eaa0f-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
