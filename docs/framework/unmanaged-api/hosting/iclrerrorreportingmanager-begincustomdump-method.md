---
title: ICLRErrorReportingManager::BeginCustomDump — Metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cb6cd8d31e01ea2f1749a6cb4d17173679f0c06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984792"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="aaa73-102">ICLRErrorReportingManager::BeginCustomDump — Metoda</span><span class="sxs-lookup"><span data-stu-id="aaa73-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="aaa73-103">Określa konfigurację zrzutów stosu niestandardowych dla usługi raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="aaa73-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa73-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aaa73-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaa73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aaa73-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="aaa73-106">[in] A [ecustomdumpflavor —](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) wartość wskazującą rodzaj zrzutu sterty, na którym można utworzyć zrzutu sterty niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="aaa73-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="aaa73-107">[in] Długość `items` tablicy.</span><span class="sxs-lookup"><span data-stu-id="aaa73-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="aaa73-108">Jeśli `dwFlavor` nie jest DUMP_FLAVOR_Mini, `dwNumItems` powinna wynosić zero.</span><span class="sxs-lookup"><span data-stu-id="aaa73-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="aaa73-109">[in] Tablica [customdumpitem —](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) wystąpień, określając elementy do dodania do minizrzut.</span><span class="sxs-lookup"><span data-stu-id="aaa73-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="aaa73-110">Jeśli `dwFlavor` nie jest DUMP_FLAVOR_Mini, `items` powinien mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="aaa73-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="aaa73-111">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="aaa73-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaa73-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aaa73-112">Return Value</span></span>  
  
|<span data-ttu-id="aaa73-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aaa73-113">HRESULT</span></span>|<span data-ttu-id="aaa73-114">Opis</span><span class="sxs-lookup"><span data-stu-id="aaa73-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aaa73-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="aaa73-115">S_OK</span></span>|<span data-ttu-id="aaa73-116">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aaa73-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="aaa73-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aaa73-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aaa73-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="aaa73-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aaa73-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aaa73-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aaa73-120">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="aaa73-120">The call timed out.</span></span>|  
|<span data-ttu-id="aaa73-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aaa73-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aaa73-122">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="aaa73-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aaa73-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aaa73-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aaa73-124">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="aaa73-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aaa73-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aaa73-125">E_FAIL</span></span>|<span data-ttu-id="aaa73-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aaa73-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aaa73-127">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="aaa73-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aaa73-128">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aaa73-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaa73-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aaa73-129">Remarks</span></span>  
 <span data-ttu-id="aaa73-130">`BeginCustomDump` Metody Ustawia konfigurację zrzutu sterty niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="aaa73-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="aaa73-131">[Endcustomdump —](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) metoda czyści konfiguracji zrzutu sterty niestandardowych i zwalnia każdy stan skojarzony.</span><span class="sxs-lookup"><span data-stu-id="aaa73-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="aaa73-132">Powinna być wywoływana po wykonaniu zrzutu sterty niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="aaa73-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aaa73-133">Nie można wywołać `EndCustomDump` powoduje, że przecieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="aaa73-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaa73-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aaa73-134">Requirements</span></span>  
 <span data-ttu-id="aaa73-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaa73-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaa73-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aaa73-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aaa73-137">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aaa73-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aaa73-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa73-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa73-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aaa73-139">See also</span></span>

- [<span data-ttu-id="aaa73-140">CustomDumpItem, struktura</span><span class="sxs-lookup"><span data-stu-id="aaa73-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="aaa73-141">ECustomDumpFlavor, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="aaa73-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="aaa73-142">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aaa73-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
