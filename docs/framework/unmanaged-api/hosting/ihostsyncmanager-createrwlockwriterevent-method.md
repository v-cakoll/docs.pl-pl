---
title: IHostSyncManager::CreateRWLockWriterEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
ms.openlocfilehash: f00d166541f7955516e9d5c1dce2a4342c08ad0a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803146"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="4def2-102">IHostSyncManager::CreateRWLockWriterEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="4def2-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="4def2-103">Tworzy obiekt zdarzenia autoresetowania dla implementacji blokady składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="4def2-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4def2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4def2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4def2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4def2-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="4def2-106">podczas Plik cookie, który ma zostać skojarzony ze zdarzeniem resetowania.</span><span class="sxs-lookup"><span data-stu-id="4def2-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="4def2-107">określoną Wskaźnik do adresu wystąpienia [IHostAutoEvent](ihostautoevent-interface.md) lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4def2-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4def2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4def2-108">Return Value</span></span>  
  
|<span data-ttu-id="4def2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4def2-109">HRESULT</span></span>|<span data-ttu-id="4def2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4def2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4def2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4def2-111">S_OK</span></span>|<span data-ttu-id="4def2-112">`CreateRWLockWriterEvent`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="4def2-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="4def2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4def2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4def2-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4def2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4def2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4def2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4def2-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="4def2-116">The call timed out.</span></span>|  
|<span data-ttu-id="4def2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4def2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4def2-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="4def2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4def2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4def2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4def2-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="4def2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4def2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4def2-121">E_FAIL</span></span>|<span data-ttu-id="4def2-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4def2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4def2-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="4def2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4def2-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4def2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4def2-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4def2-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4def2-126">Za mało dostępnej pamięci, aby utworzyć żądany obiekt zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4def2-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4def2-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4def2-127">Remarks</span></span>  
 <span data-ttu-id="4def2-128">Środowisko CLR wywołuje `CreateRWLockWriterEvent` metodę, aby uzyskać odwołanie do wystąpienia, `IHostAutoEvent` które ma być używane w jego implementacji blokady składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="4def2-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="4def2-129">Host może użyć określonego pliku cookie, aby określić, które zadania oczekują na blokadę, wywołując metody iteracji interfejsu [ICLRSyncManager](iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4def2-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4def2-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4def2-130">Requirements</span></span>  
 <span data-ttu-id="4def2-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4def2-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4def2-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4def2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4def2-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4def2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4def2-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4def2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4def2-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4def2-135">See also</span></span>

- [<span data-ttu-id="4def2-136">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4def2-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="4def2-137">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4def2-137">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="4def2-138">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="4def2-138">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="4def2-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4def2-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
