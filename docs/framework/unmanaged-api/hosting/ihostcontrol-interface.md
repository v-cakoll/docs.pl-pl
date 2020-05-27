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
ms.openlocfilehash: 9dd89abb332853b966aa81dc506099b7af6ca3b2
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804936"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="3def1-102">IHostControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3def1-102">IHostControl Interface</span></span>
<span data-ttu-id="3def1-103">Zapewnia metody konfigurowania ładowania zestawów i określania interfejsów hostingu obsługiwanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="3def1-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3def1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3def1-104">Methods</span></span>  
  
|<span data-ttu-id="3def1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3def1-105">Method</span></span>|<span data-ttu-id="3def1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3def1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3def1-107">GetHostManager, metoda</span><span class="sxs-lookup"><span data-stu-id="3def1-107">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="3def1-108">Pobiera wskaźnik interfejsu do implementacji hosta interfejsu z określonym `IID` .</span><span class="sxs-lookup"><span data-stu-id="3def1-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="3def1-109">SetAppDomainManager, metoda</span><span class="sxs-lookup"><span data-stu-id="3def1-109">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="3def1-110">Powiadamia hosta o utworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3def1-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3def1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3def1-111">Requirements</span></span>  
 <span data-ttu-id="3def1-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3def1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3def1-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3def1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3def1-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3def1-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3def1-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3def1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3def1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3def1-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="3def1-117">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="3def1-117">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="3def1-118">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3def1-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="3def1-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3def1-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
