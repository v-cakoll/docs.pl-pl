---
title: "ICLRErrorReportingManager::BeginCustomDump — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.BeginCustomDump
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c90357f969b19c767d4bb45d4d3105f50cd5682a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="7d832-102">ICLRErrorReportingManager::BeginCustomDump — Metoda</span><span class="sxs-lookup"><span data-stu-id="7d832-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="7d832-103">Określa konfigurację zrzuty stosu niestandardowych dla usługi raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="7d832-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d832-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d832-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d832-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d832-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="7d832-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) wartość, która wskazuje rodzaj zrzutu sterty umożliwiającego tworzenie zrzutu sterty niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7d832-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="7d832-107">[in] Długość `items` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7d832-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="7d832-108">Jeśli `dwFlavor` DUMP_FLAVOR_Mini, nie jest `dwNumItems` powinna wynosić zero.</span><span class="sxs-lookup"><span data-stu-id="7d832-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="7d832-109">[in] Tablica [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) wystąpień, określając elementy do dodania do mini zrzutu.</span><span class="sxs-lookup"><span data-stu-id="7d832-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="7d832-110">Jeśli `dwFlavor` DUMP_FLAVOR_Mini, nie jest `items` może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="7d832-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="7d832-111">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="7d832-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d832-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7d832-112">Return Value</span></span>  
  
|<span data-ttu-id="7d832-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d832-113">HRESULT</span></span>|<span data-ttu-id="7d832-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7d832-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d832-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d832-115">S_OK</span></span>|<span data-ttu-id="7d832-116">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7d832-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="7d832-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d832-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d832-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="7d832-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d832-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d832-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d832-120">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="7d832-120">The call timed out.</span></span>|  
|<span data-ttu-id="7d832-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d832-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d832-122">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7d832-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d832-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d832-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d832-124">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="7d832-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d832-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d832-125">E_FAIL</span></span>|<span data-ttu-id="7d832-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7d832-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d832-127">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="7d832-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d832-128">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7d832-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d832-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d832-129">Remarks</span></span>  
 <span data-ttu-id="7d832-130">`BeginCustomDump` Metody Ustawia konfigurację zrzutu sterty niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7d832-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="7d832-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) metody czyści konfiguracji zrzutu sterty niestandardowych i zwalnia każdy stan skojarzony.</span><span class="sxs-lookup"><span data-stu-id="7d832-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="7d832-132">Należy wywołać po wykonaniu zrzutu sterty niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7d832-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d832-133">Nie można wywołać `EndCustomDump` powoduje, że nastąpił przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="7d832-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d832-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d832-134">Requirements</span></span>  
 <span data-ttu-id="7d832-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d832-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d832-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d832-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d832-137">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d832-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d832-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d832-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d832-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d832-139">See Also</span></span>  
 [<span data-ttu-id="7d832-140">CustomDumpItem — struktura</span><span class="sxs-lookup"><span data-stu-id="7d832-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="7d832-141">ECustomDumpFlavor — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7d832-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="7d832-142">ICLRErrorReportingManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="7d832-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
