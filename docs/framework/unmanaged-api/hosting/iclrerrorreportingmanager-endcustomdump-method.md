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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c2d2e5454a26111748f9676cfe1ce5caa76cad5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772837"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="76e03-102">ICLRErrorReportingManager::EndCustomDump — Metoda</span><span class="sxs-lookup"><span data-stu-id="76e03-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="76e03-103">Usuwa konfigurację zrzutu niestandardowe stosu, który został określony we wcześniejszym wywołaniem [iclrerrorreportingmanager::begincustomdump —](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="76e03-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76e03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76e03-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="76e03-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="76e03-105">Return Value</span></span>  
  
|<span data-ttu-id="76e03-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76e03-106">HRESULT</span></span>|<span data-ttu-id="76e03-107">Opis</span><span class="sxs-lookup"><span data-stu-id="76e03-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76e03-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="76e03-108">S_OK</span></span>|<span data-ttu-id="76e03-109">`EndCustomDump` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="76e03-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="76e03-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76e03-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76e03-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="76e03-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76e03-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76e03-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76e03-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="76e03-113">The call timed out.</span></span>|  
|<span data-ttu-id="76e03-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76e03-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76e03-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="76e03-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76e03-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76e03-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76e03-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="76e03-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76e03-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76e03-118">E_FAIL</span></span>|<span data-ttu-id="76e03-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="76e03-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76e03-120">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="76e03-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76e03-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="76e03-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76e03-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76e03-122">Remarks</span></span>  
 <span data-ttu-id="76e03-123">`EndCustomDump` Metoda czyści Konfiguracja zrzutu niestandardowe stosu, które są ustawiane przez podczas wcześniejszego wywołania `BeginCustomDump` metody i zwalnia każdy stan skojarzony.</span><span class="sxs-lookup"><span data-stu-id="76e03-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="76e03-124">Powinna zostać wywołana po ukończeniu zrzut stosu niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="76e03-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="76e03-125">Nie można wywołać `EndCustomDump` powoduje, że przecieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="76e03-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76e03-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76e03-126">Requirements</span></span>  
 <span data-ttu-id="76e03-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76e03-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76e03-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="76e03-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76e03-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="76e03-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76e03-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76e03-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e03-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76e03-131">See also</span></span>

- [<span data-ttu-id="76e03-132">CustomDumpItem, struktura</span><span class="sxs-lookup"><span data-stu-id="76e03-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="76e03-133">ECustomDumpFlavor, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="76e03-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="76e03-134">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="76e03-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
