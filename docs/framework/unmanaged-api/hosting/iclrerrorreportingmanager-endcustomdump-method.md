---
title: "ICLRErrorReportingManager::EndCustomDump — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 709ef121294a92353b21363ae12919e8e147efab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="a927b-102">ICLRErrorReportingManager::EndCustomDump — Metoda</span><span class="sxs-lookup"><span data-stu-id="a927b-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="a927b-103">Usuwa Konfiguracja zrzutu niestandardowych stosu, który został określony we wcześniejszych wywołanie [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a927b-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a927b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a927b-104">Syntax</span></span>  
  
```  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a927b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a927b-105">Return Value</span></span>  
  
|<span data-ttu-id="a927b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a927b-106">HRESULT</span></span>|<span data-ttu-id="a927b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a927b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a927b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a927b-108">S_OK</span></span>|<span data-ttu-id="a927b-109">`EndCustomDump`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a927b-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="a927b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a927b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a927b-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a927b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a927b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a927b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a927b-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a927b-113">The call timed out.</span></span>|  
|<span data-ttu-id="a927b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a927b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a927b-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a927b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a927b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a927b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a927b-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a927b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a927b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a927b-118">E_FAIL</span></span>|<span data-ttu-id="a927b-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a927b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a927b-120">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a927b-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a927b-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a927b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a927b-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a927b-122">Remarks</span></span>  
 <span data-ttu-id="a927b-123">`EndCustomDump` Metody czyści konfiguracji zrzutu stosu niestandardowy ustawiony przez wywołanie wcześniejszych `BeginCustomDump` — metoda i zwalnia każdy stan skojarzony.</span><span class="sxs-lookup"><span data-stu-id="a927b-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="a927b-124">Należy wywołać po wykonaniu zrzutu stosu niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a927b-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a927b-125">Nie można wywołać `EndCustomDump` powoduje, że nastąpił przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="a927b-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a927b-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a927b-126">Requirements</span></span>  
 <span data-ttu-id="a927b-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a927b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a927b-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a927b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a927b-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a927b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a927b-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a927b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a927b-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a927b-131">See Also</span></span>  
 [<span data-ttu-id="a927b-132">CustomDumpItem, struktura</span><span class="sxs-lookup"><span data-stu-id="a927b-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="a927b-133">ECustomDumpFlavor, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a927b-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="a927b-134">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a927b-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
