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
ms.openlocfilehash: a20b79dd5eda9c431511cc49e7e3adaa9486b2aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155990"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="6dc00-102">ICLRErrorReportingManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6dc00-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="6dc00-103">Udostępnia metody, które umożliwiają hosta skonfigurować zrzuty stosu niestandardowych dla usługi raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="6dc00-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6dc00-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6dc00-104">Methods</span></span>  
  
|<span data-ttu-id="6dc00-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6dc00-105">Method</span></span>|<span data-ttu-id="6dc00-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6dc00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6dc00-107">BeginCustomDump, metoda</span><span class="sxs-lookup"><span data-stu-id="6dc00-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="6dc00-108">Określa konfigurację zrzuty stosu niestandardowych dla usługi raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="6dc00-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="6dc00-109">EndCustomDump, metoda</span><span class="sxs-lookup"><span data-stu-id="6dc00-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="6dc00-110">Czyści Konfiguracja zrzutu niestandardowe stosu, która została ustawiona przez podczas wcześniejszego wywołania `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="6dc00-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="6dc00-111">GetBucketParametersForCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="6dc00-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="6dc00-112">Pobiera pakiet programu Watson bieżący wyjątek w wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6dc00-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dc00-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6dc00-113">Remarks</span></span>  
 <span data-ttu-id="6dc00-114">`BeginCustomDump` Metody Ustawia konfigurację zrzut stosu niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6dc00-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="6dc00-115">`EndCustomDump` Metoda czyści Konfiguracja zrzut stosu niestandardowych i zwalnia każdy stan skojarzony.</span><span class="sxs-lookup"><span data-stu-id="6dc00-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="6dc00-116">Powinna być wywoływana po wykonaniu zrzutu niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6dc00-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6dc00-117">Nie można wywołać `EndCustomDump` powoduje, że przecieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="6dc00-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dc00-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6dc00-118">Requirements</span></span>  
 <span data-ttu-id="6dc00-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dc00-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dc00-120">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6dc00-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6dc00-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6dc00-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6dc00-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6dc00-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6dc00-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dc00-123">See also</span></span>

- [<span data-ttu-id="6dc00-124">ECustomDumpItemKind — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6dc00-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="6dc00-125">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="6dc00-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
