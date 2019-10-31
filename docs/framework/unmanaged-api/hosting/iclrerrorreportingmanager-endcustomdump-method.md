---
title: ICLRErrorReportingManager::EndCustomDump — Metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: 2acbe72377e4c5b291ab062fcb5faa6503bd7937
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129293"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="fbbcc-102">ICLRErrorReportingManager::EndCustomDump — Metoda</span><span class="sxs-lookup"><span data-stu-id="fbbcc-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="fbbcc-103">Usuwa konfigurację niestandardowego zrzutu stosu, która została określona we wcześniejszym wywołaniu metody [ICLRErrorReportingManager:: BeginCustomDump —](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fbbcc-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbbcc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbbcc-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fbbcc-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fbbcc-105">Return Value</span></span>  
  
|<span data-ttu-id="fbbcc-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbbcc-106">HRESULT</span></span>|<span data-ttu-id="fbbcc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fbbcc-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbbcc-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbbcc-108">S_OK</span></span>|<span data-ttu-id="fbbcc-109">`EndCustomDump` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="fbbcc-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fbbcc-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fbbcc-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fbbcc-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fbbcc-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fbbcc-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-113">The call timed out.</span></span>|  
|<span data-ttu-id="fbbcc-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fbbcc-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fbbcc-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fbbcc-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fbbcc-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fbbcc-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fbbcc-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fbbcc-118">E_FAIL</span></span>|<span data-ttu-id="fbbcc-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fbbcc-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fbbcc-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbbcc-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fbbcc-122">Remarks</span></span>  
 <span data-ttu-id="fbbcc-123">Metoda `EndCustomDump` czyści konfigurację niestandardowego zrzutu stosu ustawioną przez wcześniejsze wywołanie metody `BeginCustomDump` i zwalnia wszystkie powiązane Stany.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="fbbcc-124">Powinien być wywoływany po zakończeniu niestandardowego zrzutu stosu.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fbbcc-125">Nie można wywołać `EndCustomDump` powoduje przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="fbbcc-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbbcc-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fbbcc-126">Requirements</span></span>  
 <span data-ttu-id="fbbcc-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbbcc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbbcc-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fbbcc-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbbcc-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fbbcc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbbcc-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbbcc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbcc-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbbcc-131">See also</span></span>

- [<span data-ttu-id="fbbcc-132">CustomDumpItem, struktura</span><span class="sxs-lookup"><span data-stu-id="fbbcc-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="fbbcc-133">ECustomDumpFlavor, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fbbcc-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="fbbcc-134">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbbcc-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
