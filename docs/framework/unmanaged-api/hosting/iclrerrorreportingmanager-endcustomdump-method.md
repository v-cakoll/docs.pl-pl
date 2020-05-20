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
ms.openlocfilehash: 704d8d0921e671e4172fa6e0ae3f14c4908f289a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615660"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="4d7f9-102">ICLRErrorReportingManager::EndCustomDump — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d7f9-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="4d7f9-103">Usuwa konfigurację niestandardowego zrzutu stosu, która została określona we wcześniejszym wywołaniu metody [ICLRErrorReportingManager:: BeginCustomDump —](iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4d7f9-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d7f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d7f9-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4d7f9-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4d7f9-105">Return Value</span></span>  
  
|<span data-ttu-id="4d7f9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d7f9-106">HRESULT</span></span>|<span data-ttu-id="4d7f9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4d7f9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d7f9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4d7f9-108">S_OK</span></span>|<span data-ttu-id="4d7f9-109">`EndCustomDump`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="4d7f9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4d7f9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4d7f9-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4d7f9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4d7f9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4d7f9-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-113">The call timed out.</span></span>|  
|<span data-ttu-id="4d7f9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4d7f9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4d7f9-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4d7f9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4d7f9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4d7f9-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4d7f9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4d7f9-118">E_FAIL</span></span>|<span data-ttu-id="4d7f9-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4d7f9-120">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4d7f9-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d7f9-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d7f9-122">Remarks</span></span>  
 <span data-ttu-id="4d7f9-123">`EndCustomDump`Metoda czyści konfigurację niestandardowego zrzutu stosu ustawioną przez wcześniejsze wywołanie `BeginCustomDump` metody i zwalnia wszystkie powiązane Stany.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="4d7f9-124">Powinien być wywoływany po zakończeniu niestandardowego zrzutu stosu.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4d7f9-125">Niepowodzenie wywołania `EndCustomDump` powoduje przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="4d7f9-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d7f9-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d7f9-126">Requirements</span></span>  
 <span data-ttu-id="4d7f9-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d7f9-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d7f9-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4d7f9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d7f9-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4d7f9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d7f9-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d7f9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7f9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d7f9-131">See also</span></span>

- [<span data-ttu-id="4d7f9-132">CustomDumpItem, struktura</span><span class="sxs-lookup"><span data-stu-id="4d7f9-132">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="4d7f9-133">ECustomDumpFlavor — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4d7f9-133">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="4d7f9-134">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d7f9-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
