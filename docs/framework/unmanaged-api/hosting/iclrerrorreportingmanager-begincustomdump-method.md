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
ms.openlocfilehash: 7153ac214ab99228ac9c59032aa8248d06d14c3b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129295"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="1a9aa-102">ICLRErrorReportingManager::BeginCustomDump — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a9aa-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="1a9aa-103">Określa konfigurację niestandardowych zrzutów sterty dla raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a9aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a9aa-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a9aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a9aa-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="1a9aa-106">podczas Wartość [ECustomDumpFlavor —](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) , która wskazuje rodzaj zrzutu sterty, na którym ma zostać skompilowany zrzut sterty niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="1a9aa-107">podczas Długość tablicy `items`.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="1a9aa-108">Jeśli `dwFlavor` nie jest DUMP_FLAVOR_Mini, `dwNumItems` powinna być równa zero.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="1a9aa-109">podczas Tablica wystąpień [CustomDumpItem —](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) , określająca elementy, które mają zostać dodane do mini zrzutu.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="1a9aa-110">Jeśli `dwFlavor` nie jest DUMP_FLAVOR_Mini, `items` powinna mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="1a9aa-111">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a9aa-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1a9aa-112">Return Value</span></span>  
  
|<span data-ttu-id="1a9aa-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a9aa-113">HRESULT</span></span>|<span data-ttu-id="1a9aa-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1a9aa-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a9aa-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a9aa-115">S_OK</span></span>|<span data-ttu-id="1a9aa-116">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="1a9aa-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1a9aa-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1a9aa-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1a9aa-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1a9aa-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1a9aa-120">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-120">The call timed out.</span></span>|  
|<span data-ttu-id="1a9aa-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1a9aa-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1a9aa-122">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1a9aa-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1a9aa-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1a9aa-124">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1a9aa-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1a9aa-125">E_FAIL</span></span>|<span data-ttu-id="1a9aa-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1a9aa-127">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1a9aa-128">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a9aa-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a9aa-129">Remarks</span></span>  
 <span data-ttu-id="1a9aa-130">Metoda `BeginCustomDump` ustawia niestandardową konfigurację zrzutu sterty.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="1a9aa-131">Metoda [EndCustomDump —](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) czyści konfigurację zrzutu sterty niestandardowej i zwalnia wszystkie skojarzone Stany.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="1a9aa-132">Powinien być wywoływany po zakończeniu niestandardowego zrzutu sterty.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a9aa-133">Nie można wywołać `EndCustomDump` powoduje przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="1a9aa-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a9aa-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a9aa-134">Requirements</span></span>  
 <span data-ttu-id="1a9aa-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a9aa-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a9aa-136">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a9aa-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a9aa-137">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1a9aa-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a9aa-138">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a9aa-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a9aa-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a9aa-139">See also</span></span>

- [<span data-ttu-id="1a9aa-140">CustomDumpItem, struktura</span><span class="sxs-lookup"><span data-stu-id="1a9aa-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="1a9aa-141">ECustomDumpFlavor, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1a9aa-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="1a9aa-142">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a9aa-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
