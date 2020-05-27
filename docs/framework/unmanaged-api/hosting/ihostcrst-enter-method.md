---
title: IHostCrst::Enter — Metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
ms.openlocfilehash: 79afaac4dce1c4baa9802d81af90c425f5de7a08
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804920"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="243ae-102">IHostCrst::Enter — Metoda</span><span class="sxs-lookup"><span data-stu-id="243ae-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="243ae-103">Wprowadza sekcję krytyczną, która jest reprezentowana przez bieżące wystąpienie [IHostCrst](ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="243ae-103">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="243ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="243ae-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="243ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="243ae-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="243ae-106">podczas Jeden z wartości [WAIT_OPTION](wait-option-enumeration.md) , wskazujący, jaka akcja powinna zostać podjęta przez hosta, jeśli operacja jest blokowana.</span><span class="sxs-lookup"><span data-stu-id="243ae-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="243ae-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="243ae-107">Return Value</span></span>  
  
|<span data-ttu-id="243ae-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="243ae-108">HRESULT</span></span>|<span data-ttu-id="243ae-109">Opis</span><span class="sxs-lookup"><span data-stu-id="243ae-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="243ae-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="243ae-110">S_OK</span></span>|<span data-ttu-id="243ae-111">`Enter`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="243ae-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="243ae-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="243ae-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="243ae-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="243ae-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="243ae-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="243ae-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="243ae-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="243ae-115">The call timed out.</span></span>|  
|<span data-ttu-id="243ae-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="243ae-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="243ae-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="243ae-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="243ae-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="243ae-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="243ae-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="243ae-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="243ae-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="243ae-120">E_FAIL</span></span>|<span data-ttu-id="243ae-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="243ae-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="243ae-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="243ae-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="243ae-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="243ae-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="243ae-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="243ae-124">Remarks</span></span>  
 <span data-ttu-id="243ae-125">`Enter`odzwierciedla funkcję Win32 `EnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="243ae-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="243ae-126">Ta metoda nie jest zwracana do momentu wprowadzenia sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="243ae-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="243ae-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="243ae-127">Requirements</span></span>  
 <span data-ttu-id="243ae-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="243ae-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="243ae-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="243ae-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="243ae-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="243ae-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="243ae-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="243ae-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="243ae-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="243ae-132">See also</span></span>

- [<span data-ttu-id="243ae-133">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="243ae-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="243ae-134">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="243ae-134">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="243ae-135">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="243ae-135">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
