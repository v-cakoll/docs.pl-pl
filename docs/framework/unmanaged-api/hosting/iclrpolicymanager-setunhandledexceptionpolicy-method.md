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
ms.openlocfilehash: 7fa02c4c79da118543117aada7d1b9cca09c4cae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703403"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="50ccb-102">ICLRPolicyManager::SetUnhandledExceptionPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="50ccb-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="50ccb-103">Określa zachowanie środowiska uruchomieniowego języka wspólnego (CLR) w przypadku wystąpienia nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="50ccb-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50ccb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50ccb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50ccb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50ccb-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="50ccb-106">podczas Jedna z wartości [EClrUnhandledException —](eclrunhandledexception-enumeration.md) , wskazująca, czy zachowanie jest ustawione przez środowisko CLR czy hosta.</span><span class="sxs-lookup"><span data-stu-id="50ccb-106">[in] One of the [EClrUnhandledException](eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50ccb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50ccb-107">Return Value</span></span>  
  
|<span data-ttu-id="50ccb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50ccb-108">HRESULT</span></span>|<span data-ttu-id="50ccb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="50ccb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50ccb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="50ccb-110">S_OK</span></span>|<span data-ttu-id="50ccb-111">`SetUnhandledExceptionPolicy`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="50ccb-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="50ccb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50ccb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50ccb-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="50ccb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50ccb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50ccb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50ccb-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="50ccb-115">The call timed out.</span></span>|  
|<span data-ttu-id="50ccb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50ccb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50ccb-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="50ccb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50ccb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50ccb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50ccb-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="50ccb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50ccb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50ccb-120">E_FAIL</span></span>|<span data-ttu-id="50ccb-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="50ccb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50ccb-122">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="50ccb-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50ccb-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="50ccb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50ccb-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50ccb-124">Remarks</span></span>  
 <span data-ttu-id="50ccb-125">Domyślnie środowisko CLR jest ostatnim programem obsługi dla wszystkich nieobsłużonych wyjątków, a jego domyślne zachowanie polega na rozdzieleniu tego procesu.</span><span class="sxs-lookup"><span data-stu-id="50ccb-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="50ccb-126">Na hoście można zmienić to zachowanie, ustawiając `policy` wartość na eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="50ccb-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="50ccb-127">Ta wartość umożliwia hostowi wdrożenie własnego zachowania domyślnego, tak jak w przypadku wcześniejszych wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="50ccb-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ccb-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50ccb-128">Requirements</span></span>  
 <span data-ttu-id="50ccb-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50ccb-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50ccb-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="50ccb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50ccb-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="50ccb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50ccb-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50ccb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ccb-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50ccb-133">See also</span></span>

- [<span data-ttu-id="50ccb-134">EClrUnhandledException — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="50ccb-134">EClrUnhandledException Enumeration</span></span>](eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="50ccb-135">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="50ccb-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="50ccb-136">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="50ccb-136">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="50ccb-137">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="50ccb-137">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
