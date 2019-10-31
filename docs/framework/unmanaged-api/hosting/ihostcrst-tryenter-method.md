---
title: IHostCrst::TryEnter — Metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
ms.openlocfilehash: f4b40a595bbdea4dd390a42af6a0d4b1a5efa2f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130492"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="872e5-102">IHostCrst::TryEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="872e5-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="872e5-103">Próbuje wprowadzić sekcję krytyczną reprezentowaną przez bieżące wystąpienie [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="872e5-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="872e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="872e5-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="872e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="872e5-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="872e5-106">podczas Jedna z wartości [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , wskazująca, jaka akcja powinna być wykonywana przez hosta, jeśli operacja jest blokowana.</span><span class="sxs-lookup"><span data-stu-id="872e5-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="872e5-107">[out] `true` czy można wprowadzić sekcję krytyczną; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="872e5-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="872e5-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="872e5-108">Return Value</span></span>  
  
|<span data-ttu-id="872e5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="872e5-109">HRESULT</span></span>|<span data-ttu-id="872e5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="872e5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="872e5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="872e5-111">S_OK</span></span>|<span data-ttu-id="872e5-112">`TryEnter` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="872e5-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="872e5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="872e5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="872e5-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="872e5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="872e5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="872e5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="872e5-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="872e5-116">The call timed out.</span></span>|  
|<span data-ttu-id="872e5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="872e5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="872e5-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="872e5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="872e5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="872e5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="872e5-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="872e5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="872e5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="872e5-121">E_FAIL</span></span>|<span data-ttu-id="872e5-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="872e5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="872e5-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="872e5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="872e5-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="872e5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="872e5-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="872e5-125">Remarks</span></span>  
 <span data-ttu-id="872e5-126">`TryEnter` zwraca natychmiast i wskazuje, czy wywołujący wątek wszedł do sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="872e5-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="872e5-127">Ta metoda odzwierciedla funkcję Wind32 `TryEnterCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="872e5-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="872e5-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="872e5-128">Requirements</span></span>  
 <span data-ttu-id="872e5-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="872e5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="872e5-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="872e5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="872e5-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="872e5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="872e5-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="872e5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872e5-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="872e5-133">See also</span></span>

- [<span data-ttu-id="872e5-134">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="872e5-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="872e5-135">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="872e5-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="872e5-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="872e5-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
