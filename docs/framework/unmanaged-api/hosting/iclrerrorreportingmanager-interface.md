---
title: ICLRErrorReportingManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a9d9cff0360e4eb27584fe0f22c1c20396ff8f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966257"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="1c6e5-102">ICLRErrorReportingManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1c6e5-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="1c6e5-103">Dostarcza metody, które umożliwiają hostowi skonfigurowanie niestandardowych zrzutów stosu na potrzeby raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="1c6e5-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c6e5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1c6e5-104">Methods</span></span>  
  
|<span data-ttu-id="1c6e5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1c6e5-105">Method</span></span>|<span data-ttu-id="1c6e5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1c6e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c6e5-107">BeginCustomDump, metoda</span><span class="sxs-lookup"><span data-stu-id="1c6e5-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="1c6e5-108">Określa konfigurację niestandardowych zrzutów stosu dla raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="1c6e5-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="1c6e5-109">EndCustomDump, metoda</span><span class="sxs-lookup"><span data-stu-id="1c6e5-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="1c6e5-110">Czyści konfigurację niestandardowego zrzutu stosu ustawioną w ramach wcześniejszego wywołania do `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="1c6e5-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="1c6e5-111">GetBucketParametersForCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="1c6e5-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="1c6e5-112">Pobiera pakiet programu Watson dla bieżącego wyjątku w wątku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="1c6e5-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c6e5-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c6e5-113">Remarks</span></span>  
 <span data-ttu-id="1c6e5-114">`BeginCustomDump` Metoda ustawia konfigurację niestandardowego zrzutu stosu.</span><span class="sxs-lookup"><span data-stu-id="1c6e5-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="1c6e5-115">`EndCustomDump` Metoda czyści konfigurację niestandardowego zrzutu stosu i zwalnia wszystkie powiązane Stany.</span><span class="sxs-lookup"><span data-stu-id="1c6e5-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="1c6e5-116">Powinien być wywoływany po zakończeniu niestandardowego zrzutu.</span><span class="sxs-lookup"><span data-stu-id="1c6e5-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1c6e5-117">Niepowodzenie wywołania `EndCustomDump` powoduje przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="1c6e5-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c6e5-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c6e5-118">Requirements</span></span>  
 <span data-ttu-id="1c6e5-119">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c6e5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c6e5-120">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1c6e5-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c6e5-121">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1c6e5-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c6e5-122">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c6e5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c6e5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c6e5-123">See also</span></span>

- [<span data-ttu-id="1c6e5-124">ECustomDumpItemKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1c6e5-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="1c6e5-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1c6e5-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
