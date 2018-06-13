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
ms.openlocfilehash: b5d58a90901b7d7cb80ea7f25401b857b4d4875e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434515"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="3ae4d-102">ICLRErrorReportingManager::BeginCustomDump — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ae4d-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="3ae4d-103">Określa konfigurację zrzuty stosu niestandardowych dla usługi raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ae4d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ae4d-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ae4d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ae4d-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="3ae4d-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) wartość, która wskazuje rodzaj zrzutu sterty umożliwiającego tworzenie zrzutu sterty niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="3ae4d-107">[in] Długość `items` tablicy.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="3ae4d-108">Jeśli `dwFlavor` DUMP_FLAVOR_Mini, nie jest `dwNumItems` powinna wynosić zero.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="3ae4d-109">[in] Tablica [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) wystąpień, określając elementy do dodania do mini zrzutu.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="3ae4d-110">Jeśli `dwFlavor` DUMP_FLAVOR_Mini, nie jest `items` może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="3ae4d-111">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ae4d-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3ae4d-112">Return Value</span></span>  
  
|<span data-ttu-id="3ae4d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ae4d-113">HRESULT</span></span>|<span data-ttu-id="3ae4d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3ae4d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ae4d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ae4d-115">S_OK</span></span>|<span data-ttu-id="3ae4d-116">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="3ae4d-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3ae4d-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3ae4d-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3ae4d-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3ae4d-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3ae4d-120">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-120">The call timed out.</span></span>|  
|<span data-ttu-id="3ae4d-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3ae4d-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3ae4d-122">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3ae4d-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3ae4d-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3ae4d-124">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3ae4d-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3ae4d-125">E_FAIL</span></span>|<span data-ttu-id="3ae4d-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3ae4d-127">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3ae4d-128">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ae4d-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ae4d-129">Remarks</span></span>  
 <span data-ttu-id="3ae4d-130">`BeginCustomDump` Metody Ustawia konfigurację zrzutu sterty niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="3ae4d-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) metody czyści konfiguracji zrzutu sterty niestandardowych i zwalnia każdy stan skojarzony.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="3ae4d-132">Należy wywołać po wykonaniu zrzutu sterty niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ae4d-133">Nie można wywołać `EndCustomDump` powoduje, że nastąpił przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ae4d-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ae4d-134">Requirements</span></span>  
 <span data-ttu-id="3ae4d-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ae4d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ae4d-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3ae4d-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ae4d-137">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ae4d-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ae4d-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ae4d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae4d-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ae4d-139">See Also</span></span>  
 [<span data-ttu-id="3ae4d-140">CustomDumpItem, struktura</span><span class="sxs-lookup"><span data-stu-id="3ae4d-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="3ae4d-141">ECustomDumpFlavor, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3ae4d-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="3ae4d-142">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3ae4d-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
