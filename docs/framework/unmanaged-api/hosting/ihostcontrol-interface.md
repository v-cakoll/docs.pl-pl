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
ms.openlocfilehash: 961f166cdb2c69e29fef4753a37edcc57c427257
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438093"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="95f65-102">IHostControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="95f65-102">IHostControl Interface</span></span>
<span data-ttu-id="95f65-103">Udostępnia metody konfigurowania ładowania zestawów i określania, które hosting interfejsy obsługuje hosta.</span><span class="sxs-lookup"><span data-stu-id="95f65-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95f65-104">Metody</span><span class="sxs-lookup"><span data-stu-id="95f65-104">Methods</span></span>  
  
|<span data-ttu-id="95f65-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="95f65-105">Method</span></span>|<span data-ttu-id="95f65-106">Opis</span><span class="sxs-lookup"><span data-stu-id="95f65-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95f65-107">GetHostManager, metoda</span><span class="sxs-lookup"><span data-stu-id="95f65-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="95f65-108">Pobiera wskaźnika interfejsu hosta implementacji interfejsu z określonym `IID`.</span><span class="sxs-lookup"><span data-stu-id="95f65-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="95f65-109">SetAppDomainManager, metoda</span><span class="sxs-lookup"><span data-stu-id="95f65-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="95f65-110">Powiadamia hosta utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95f65-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95f65-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95f65-111">Requirements</span></span>  
 <span data-ttu-id="95f65-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95f65-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95f65-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95f65-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95f65-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95f65-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95f65-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95f65-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f65-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95f65-116">See Also</span></span>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="95f65-117">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="95f65-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="95f65-118">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="95f65-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="95f65-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="95f65-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
