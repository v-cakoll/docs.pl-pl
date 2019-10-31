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
ms.openlocfilehash: 49a60b6b9b076138d8ff1f8a15041e9a6bacfede
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129254"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="26f9f-102">ICLRErrorReportingManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="26f9f-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="26f9f-103">Dostarcza metody, które umożliwiają hostowi skonfigurowanie niestandardowych zrzutów stosu na potrzeby raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="26f9f-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26f9f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="26f9f-104">Methods</span></span>  
  
|<span data-ttu-id="26f9f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="26f9f-105">Method</span></span>|<span data-ttu-id="26f9f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="26f9f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26f9f-107">BeginCustomDump, metoda</span><span class="sxs-lookup"><span data-stu-id="26f9f-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="26f9f-108">Określa konfigurację niestandardowych zrzutów stosu dla raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="26f9f-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="26f9f-109">EndCustomDump, metoda</span><span class="sxs-lookup"><span data-stu-id="26f9f-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="26f9f-110">Czyści konfigurację niestandardowego zrzutu stosu ustawioną przez wcześniejsze wywołanie do `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="26f9f-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="26f9f-111">GetBucketParametersForCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="26f9f-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="26f9f-112">Pobiera pakiet programu Watson dla bieżącego wyjątku w wątku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="26f9f-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26f9f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26f9f-113">Remarks</span></span>  
 <span data-ttu-id="26f9f-114">Metoda `BeginCustomDump` ustawia konfigurację niestandardowego zrzutu stosu.</span><span class="sxs-lookup"><span data-stu-id="26f9f-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="26f9f-115">Metoda `EndCustomDump` czyści konfigurację niestandardowego zrzutu stosu i zwalnia wszystkie powiązane Stany.</span><span class="sxs-lookup"><span data-stu-id="26f9f-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="26f9f-116">Powinien być wywoływany po zakończeniu niestandardowego zrzutu.</span><span class="sxs-lookup"><span data-stu-id="26f9f-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="26f9f-117">Nie można wywołać `EndCustomDump` powoduje przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="26f9f-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26f9f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26f9f-118">Requirements</span></span>  
 <span data-ttu-id="26f9f-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f9f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26f9f-120">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26f9f-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26f9f-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26f9f-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26f9f-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26f9f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f9f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26f9f-123">See also</span></span>

- [<span data-ttu-id="26f9f-124">ECustomDumpItemKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="26f9f-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="26f9f-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="26f9f-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
