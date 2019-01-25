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
ms.openlocfilehash: 1c2b383abdc67546749867de154a00fda244b3ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660024"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="f5686-102">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5686-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="f5686-103">Zarządza listę zestawów, które są ładowane przez środowisko uruchomieniowe języka wspólnego (CLR), a nie przez hosta.</span><span class="sxs-lookup"><span data-stu-id="f5686-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5686-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f5686-104">Methods</span></span>  
  
|<span data-ttu-id="f5686-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f5686-105">Method</span></span>|<span data-ttu-id="f5686-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f5686-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5686-107">IsAssemblyReferenceInList, metoda</span><span class="sxs-lookup"><span data-stu-id="f5686-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="f5686-108">Pobiera wartość wskazującą, czy podany wskaźnik odwołuje się zestaw na liście.</span><span class="sxs-lookup"><span data-stu-id="f5686-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="f5686-109">IsStringAssemblyReferenceInList, metoda</span><span class="sxs-lookup"><span data-stu-id="f5686-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="f5686-110">Pobiera wartość wskazującą, czy podana nazwa jest zgodna z nazwą zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="f5686-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5686-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5686-111">Remarks</span></span>  
 <span data-ttu-id="f5686-112">Wywołaj [iclrassemblyidentitymanager::getclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodę, aby uzyskać wskaźnik do wystąpienia `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="f5686-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5686-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5686-113">Requirements</span></span>  
 <span data-ttu-id="f5686-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5686-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5686-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5686-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5686-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5686-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5686-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5686-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5686-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5686-118">See also</span></span>
- [<span data-ttu-id="f5686-119">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5686-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="f5686-120">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5686-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="f5686-121">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f5686-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
