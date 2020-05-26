---
title: IHostSyncManager::CreateMonitorEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: c0f7e1fd6bf4c9386300b11477df85e87899fc67
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803323"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="09ef1-102">IHostSyncManager::CreateMonitorEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="09ef1-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="09ef1-103">Tworzy monitorowany obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="09ef1-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ef1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09ef1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09ef1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09ef1-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="09ef1-106">podczas Plik cookie do skojarzenia z obiektem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="09ef1-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="09ef1-107">określoną Wskaźnik do adresu wystąpienia [IHostAutoEvent](ihostautoevent-interface.md) lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="09ef1-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09ef1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="09ef1-108">Return Value</span></span>  
  
|<span data-ttu-id="09ef1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09ef1-109">HRESULT</span></span>|<span data-ttu-id="09ef1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="09ef1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09ef1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="09ef1-111">S_OK</span></span>|<span data-ttu-id="09ef1-112">`CreateMonitorEvent`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="09ef1-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="09ef1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09ef1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09ef1-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="09ef1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="09ef1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="09ef1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="09ef1-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="09ef1-116">The call timed out.</span></span>|  
|<span data-ttu-id="09ef1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="09ef1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="09ef1-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="09ef1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="09ef1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="09ef1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="09ef1-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="09ef1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="09ef1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09ef1-121">E_FAIL</span></span>|<span data-ttu-id="09ef1-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="09ef1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="09ef1-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="09ef1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="09ef1-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="09ef1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="09ef1-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="09ef1-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="09ef1-126">Za mało dostępnej pamięci, aby utworzyć żądany obiekt zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="09ef1-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09ef1-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09ef1-127">Remarks</span></span>  
 <span data-ttu-id="09ef1-128">`CreateMonitorEvent`Zwraca wartość `IHostAutoEvent` , która jest wykorzystywana przez środowisko CLR w jej implementacji <xref:System.Threading.Monitor?displayProperty=nameWithType> typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="09ef1-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="09ef1-129">Ta metoda odzwierciedla funkcję Win32 `CreateEvent` z wartością `false` określoną dla `bManualReset` parametru.</span><span class="sxs-lookup"><span data-stu-id="09ef1-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="09ef1-130">Host może użyć pliku cookie, aby określić, które zadanie oczekuje na monitor, wywołując metodę [ICLRSyncManager:: GetMonitorOwner —](iclrsyncmanager-getmonitorowner-method.md) .</span><span class="sxs-lookup"><span data-stu-id="09ef1-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ef1-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09ef1-131">Requirements</span></span>  
 <span data-ttu-id="09ef1-132">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09ef1-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ef1-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="09ef1-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09ef1-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="09ef1-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09ef1-135">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ef1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ef1-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09ef1-136">See also</span></span>

- [<span data-ttu-id="09ef1-137">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="09ef1-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="09ef1-138">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="09ef1-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="09ef1-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="09ef1-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
