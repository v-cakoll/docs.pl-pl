---
title: ICLRDebugManager::IsDebuggerAttached — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: a21391f52a27e7f7a3abe533499c6b2581ec4a73
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615758"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="60d46-102">ICLRDebugManager::IsDebuggerAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="60d46-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="60d46-103">Pobiera wartość wskazującą, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="60d46-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60d46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60d46-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60d46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60d46-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="60d46-106">[out] `true` w przypadku dołączenia debugera do procesu; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="60d46-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60d46-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="60d46-107">Return Value</span></span>  
  
|<span data-ttu-id="60d46-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60d46-108">HRESULT</span></span>|<span data-ttu-id="60d46-109">Opis</span><span class="sxs-lookup"><span data-stu-id="60d46-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60d46-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="60d46-110">S_OK</span></span>|<span data-ttu-id="60d46-111">`IsDebuggerAttached`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="60d46-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="60d46-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60d46-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60d46-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="60d46-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="60d46-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="60d46-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="60d46-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="60d46-115">The call timed out.</span></span>|  
|<span data-ttu-id="60d46-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="60d46-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="60d46-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="60d46-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="60d46-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="60d46-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="60d46-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="60d46-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="60d46-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60d46-120">E_FAIL</span></span>|<span data-ttu-id="60d46-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="60d46-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="60d46-122">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="60d46-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="60d46-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="60d46-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60d46-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60d46-124">Remarks</span></span>  
 <span data-ttu-id="60d46-125">`IsDebuggerAttached`umożliwia hostowi zapytanie do środowiska CLR w celu określenia, czy debuger jest dołączony do procesu.</span><span class="sxs-lookup"><span data-stu-id="60d46-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60d46-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60d46-126">Requirements</span></span>  
 <span data-ttu-id="60d46-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60d46-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60d46-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="60d46-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60d46-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="60d46-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60d46-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60d46-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d46-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60d46-131">See also</span></span>

- [<span data-ttu-id="60d46-132">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="60d46-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="60d46-133">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="60d46-133">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="60d46-134">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="60d46-134">IHostControl Interface</span></span>](ihostcontrol-interface.md)
