---
title: ICLRAssemblyReferenceList — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43c40e833e3a250239e9e90667196a2a74a96e0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187658"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="22c76-102">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="22c76-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="22c76-103">Zarządza listę zestawów, które są ładowane przez środowisko uruchomieniowe języka wspólnego (CLR), a nie przez hosta.</span><span class="sxs-lookup"><span data-stu-id="22c76-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="22c76-104">Metody</span><span class="sxs-lookup"><span data-stu-id="22c76-104">Methods</span></span>  
  
|<span data-ttu-id="22c76-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="22c76-105">Method</span></span>|<span data-ttu-id="22c76-106">Opis</span><span class="sxs-lookup"><span data-stu-id="22c76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="22c76-107">IsAssemblyReferenceInList, metoda</span><span class="sxs-lookup"><span data-stu-id="22c76-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="22c76-108">Pobiera wartość wskazującą, czy podany wskaźnik odwołuje się zestaw na liście.</span><span class="sxs-lookup"><span data-stu-id="22c76-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="22c76-109">IsStringAssemblyReferenceInList, metoda</span><span class="sxs-lookup"><span data-stu-id="22c76-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="22c76-110">Pobiera wartość wskazującą, czy podana nazwa jest zgodna z nazwą zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="22c76-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22c76-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22c76-111">Remarks</span></span>  
 <span data-ttu-id="22c76-112">Wywołaj [iclrassemblyidentitymanager::getclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodę, aby uzyskać wskaźnik do wystąpienia `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="22c76-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22c76-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22c76-113">Requirements</span></span>  
 <span data-ttu-id="22c76-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22c76-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22c76-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="22c76-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22c76-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22c76-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="22c76-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="22c76-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="22c76-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22c76-118">See also</span></span>

- [<span data-ttu-id="22c76-119">ICLRAssemblyIdentityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="22c76-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="22c76-120">IHostAssemblyStore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="22c76-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="22c76-121">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="22c76-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
