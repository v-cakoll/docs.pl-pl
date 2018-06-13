---
title: IHostIoCompletionManager::InitializeHostOverlapped — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 023e112aa8273d99efce2e0f2116f95569ac0c3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438971"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="e1847-102">IHostIoCompletionManager::InitializeHostOverlapped — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1847-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="e1847-103">Zapewnia możliwość zainicjować wszelkie niestandardowe dane mają zostać dołączone do systemu Win32 hosta `OVERLAPPED` struktury, która jest używana dla żądań asynchronicznych We/Wy.</span><span class="sxs-lookup"><span data-stu-id="e1847-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1847-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1847-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1847-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1847-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="e1847-106">[in] Wskaźnik do środowiska Win32 `OVERLAPPED` struktury, które zostaną dołączone do żądania operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="e1847-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1847-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e1847-107">Return Value</span></span>  
  
|<span data-ttu-id="e1847-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1847-108">HRESULT</span></span>|<span data-ttu-id="e1847-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e1847-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1847-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1847-110">S_OK</span></span>|<span data-ttu-id="e1847-111">`InitializeHostOverlapped` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1847-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="e1847-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e1847-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e1847-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e1847-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e1847-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e1847-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e1847-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e1847-115">The call timed out.</span></span>|  
|<span data-ttu-id="e1847-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e1847-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e1847-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e1847-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e1847-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e1847-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e1847-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e1847-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e1847-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1847-120">E_FAIL</span></span>|<span data-ttu-id="e1847-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e1847-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e1847-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e1847-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e1847-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e1847-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e1847-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e1847-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e1847-125">Za mało pamięci nie była dostępna do przydzielenia do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="e1847-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1847-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1847-126">Remarks</span></span>  
 <span data-ttu-id="e1847-127">Użyj funkcji platformy Windows `OVERLAPPED` struktury do przechowywania stanu dla żądań asynchronicznych We/Wy.</span><span class="sxs-lookup"><span data-stu-id="e1847-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="e1847-128">Wywołania CLR `InitializeHostOverlapped` metody daje możliwość dołączenia danych niestandardowych do hosta `OVERLAPPED` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e1847-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e1847-129">Aby uzyskać na początku bloku ich danych niestandardowych, hosty ustawić przesunięcie rozmiar `OVERLAPPED` struktury (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="e1847-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="e1847-130">Zwracana wartość E_OUTOFMEMORY wskazuje, że host nie może zainicjować swoich danych niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e1847-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="e1847-131">W takim przypadku CLR zgłasza błąd i nie powiodło się wywołanie.</span><span class="sxs-lookup"><span data-stu-id="e1847-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1847-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1847-132">Requirements</span></span>  
 <span data-ttu-id="e1847-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1847-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1847-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e1847-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1847-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1847-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1847-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1847-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1847-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1847-137">See Also</span></span>  
 [<span data-ttu-id="e1847-138">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1847-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="e1847-139">GetHostOverlappedSize, metoda</span><span class="sxs-lookup"><span data-stu-id="e1847-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [<span data-ttu-id="e1847-140">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1847-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
