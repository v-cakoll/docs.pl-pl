---
title: ICLRDomainManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce53149b92ca40ad50ecbefaf4701940e8567ae5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103927"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="f0e7a-102">ICLRDomainManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f0e7a-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="f0e7a-103">Umożliwia hosta określić Menedżer domeny aplikacji, która będzie służyć do zainicjowania domyślnej domeny aplikacji i określić właściwości inicjowania.</span><span class="sxs-lookup"><span data-stu-id="f0e7a-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0e7a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f0e7a-104">Methods</span></span>  
  
|<span data-ttu-id="f0e7a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0e7a-105">Method</span></span>|<span data-ttu-id="f0e7a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f0e7a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0e7a-107">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="f0e7a-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="f0e7a-108">Określa typ pochodną <xref:System.AppDomainManager?displayProperty=nameWithType> klasy Menedżer domeny aplikacji, która będzie służyć do zainicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0e7a-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="f0e7a-109">SetPropertiesForDefaultAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="f0e7a-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="f0e7a-110">Ustawia właściwości, które będą używane do zainicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0e7a-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0e7a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0e7a-111">Remarks</span></span>  
 <span data-ttu-id="f0e7a-112">Aby pobrać wystąpienie tego interfejsu, należy wywołać [iclrcontrol::getclrmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody z typem Menedżera IID `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="f0e7a-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0e7a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0e7a-113">Requirements</span></span>  
 <span data-ttu-id="f0e7a-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0e7a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0e7a-115">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f0e7a-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f0e7a-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0e7a-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f0e7a-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f0e7a-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f0e7a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0e7a-118">See also</span></span>

- [<span data-ttu-id="f0e7a-119">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0e7a-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f0e7a-120">Hosting</span><span class="sxs-lookup"><span data-stu-id="f0e7a-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
