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
ms.openlocfilehash: 388b26a5559435ea57300751987d14bc5cb9d50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435300"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="75df3-102">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="75df3-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="75df3-103">Zarządza listę zestawów, które są ładowane przez środowisko uruchomieniowe języka wspólnego (CLR), a nie przez hosta.</span><span class="sxs-lookup"><span data-stu-id="75df3-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75df3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="75df3-104">Methods</span></span>  
  
|<span data-ttu-id="75df3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="75df3-105">Method</span></span>|<span data-ttu-id="75df3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="75df3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75df3-107">IsAssemblyReferenceInList, metoda</span><span class="sxs-lookup"><span data-stu-id="75df3-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="75df3-108">Pobiera wartość wskazującą, czy podany wskaźnik odwołuje się do zestawu, na liście.</span><span class="sxs-lookup"><span data-stu-id="75df3-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="75df3-109">IsStringAssemblyReferenceInList, metoda</span><span class="sxs-lookup"><span data-stu-id="75df3-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="75df3-110">Pobiera wartość wskazującą, czy podana nazwa odpowiada nazwie zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="75df3-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75df3-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75df3-111">Remarks</span></span>  
 <span data-ttu-id="75df3-112">Wywołanie [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodę, aby otrzymywać wskaźnik do wystąpienia `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="75df3-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75df3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75df3-113">Requirements</span></span>  
 <span data-ttu-id="75df3-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75df3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75df3-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75df3-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75df3-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75df3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75df3-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75df3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75df3-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75df3-118">See Also</span></span>  
 [<span data-ttu-id="75df3-119">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="75df3-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="75df3-120">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="75df3-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="75df3-121">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="75df3-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
