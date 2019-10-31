---
title: IHostControl — Interfejs
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 444a78705c61d5a53764f55185ef1a907830bd71
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195886"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="9a57e-102">IHostControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9a57e-102">IHostControl Interface</span></span>
<span data-ttu-id="9a57e-103">Zapewnia metody konfigurowania ładowania zestawów i określania interfejsów hostingu obsługiwanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="9a57e-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a57e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9a57e-104">Methods</span></span>  
  
|<span data-ttu-id="9a57e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a57e-105">Method</span></span>|<span data-ttu-id="9a57e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9a57e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a57e-107">GetHostManager, metoda</span><span class="sxs-lookup"><span data-stu-id="9a57e-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="9a57e-108">Pobiera wskaźnik interfejsu do implementacji hosta interfejsu o określonym `IID`.</span><span class="sxs-lookup"><span data-stu-id="9a57e-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="9a57e-109">SetAppDomainManager, metoda</span><span class="sxs-lookup"><span data-stu-id="9a57e-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="9a57e-110">Powiadamia hosta o utworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a57e-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a57e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a57e-111">Requirements</span></span>  
 <span data-ttu-id="9a57e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a57e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a57e-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a57e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a57e-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a57e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a57e-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a57e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a57e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a57e-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="9a57e-117">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a57e-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="9a57e-118">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a57e-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9a57e-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9a57e-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
