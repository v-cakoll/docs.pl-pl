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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 014e5c9951091046ae07374794743e82affcd5ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122268"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="912e3-102">IHostControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="912e3-102">IHostControl Interface</span></span>
<span data-ttu-id="912e3-103">Udostępnia metody do konfigurowania ładowania zestawów i podczas określania, które hostingu interfejsów obsługuje hosta.</span><span class="sxs-lookup"><span data-stu-id="912e3-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="912e3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="912e3-104">Methods</span></span>  
  
|<span data-ttu-id="912e3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="912e3-105">Method</span></span>|<span data-ttu-id="912e3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="912e3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="912e3-107">GetHostManager, metoda</span><span class="sxs-lookup"><span data-stu-id="912e3-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="912e3-108">Pobiera wskaźnik interfejsu do implementacji interfejsu hosta z określonym `IID`.</span><span class="sxs-lookup"><span data-stu-id="912e3-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="912e3-109">SetAppDomainManager, metoda</span><span class="sxs-lookup"><span data-stu-id="912e3-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="912e3-110">Powiadamia hosta, że utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="912e3-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="912e3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="912e3-111">Requirements</span></span>  
 <span data-ttu-id="912e3-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="912e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="912e3-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="912e3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="912e3-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="912e3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="912e3-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="912e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912e3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="912e3-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="912e3-117">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="912e3-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="912e3-118">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="912e3-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="912e3-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="912e3-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
