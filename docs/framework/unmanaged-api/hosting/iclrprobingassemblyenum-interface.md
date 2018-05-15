---
title: ICLRProbingAssemblyEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c295a5633dedf1f0c85a9a697fea5524ee03fafc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="e41a5-102">ICLRProbingAssemblyEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e41a5-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="e41a5-103">Udostępnia metody umożliwiające hosta można uzyskać za pomocą zestawu tożsamości informacje, które są wewnętrzne środowisko uruchomieniowe języka wspólnego (CLR), bez konieczności tworzenia i zrozumienie tej tożsamości sondowania tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="e41a5-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e41a5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e41a5-104">Methods</span></span>  
  
|<span data-ttu-id="e41a5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e41a5-105">Method</span></span>|<span data-ttu-id="e41a5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e41a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e41a5-107">Get, metoda</span><span class="sxs-lookup"><span data-stu-id="e41a5-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="e41a5-108">Pobiera tożsamość zestawu o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="e41a5-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e41a5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e41a5-109">Remarks</span></span>  
 <span data-ttu-id="e41a5-110">Metody, takie jak [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) zwracać `ICLRProbingAssemblyEnum` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e41a5-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e41a5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e41a5-111">Requirements</span></span>  
 <span data-ttu-id="e41a5-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e41a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e41a5-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e41a5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e41a5-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e41a5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e41a5-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e41a5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e41a5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e41a5-116">See Also</span></span>  
 [<span data-ttu-id="e41a5-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e41a5-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="e41a5-118">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="e41a5-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="e41a5-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e41a5-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
