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
ms.openlocfilehash: e1459c1604f3f8f043fd9b61533235ab7861c910
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120559"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="db3f6-102">ICLRProbingAssemblyEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="db3f6-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="db3f6-103">Dostarcza metody, które umożliwiają hostowi pobieranie tożsamości dla zestawu przy użyciu informacji o tożsamości zestawu, które są wewnętrzne dla środowiska uruchomieniowego języka wspólnego (CLR), bez konieczności tworzenia lub zrozumienia tożsamości.</span><span class="sxs-lookup"><span data-stu-id="db3f6-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db3f6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="db3f6-104">Methods</span></span>  
  
|<span data-ttu-id="db3f6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="db3f6-105">Method</span></span>|<span data-ttu-id="db3f6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="db3f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db3f6-107">Get, metoda</span><span class="sxs-lookup"><span data-stu-id="db3f6-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="db3f6-108">Pobiera tożsamość zestawu o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="db3f6-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db3f6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db3f6-109">Remarks</span></span>  
 <span data-ttu-id="db3f6-110">Metody, takie jak [ICLRAssemblyIdentityManager:: GetProbingAssembliesFromReference —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) , zwracają wystąpienie `ICLRProbingAssemblyEnum`.</span><span class="sxs-lookup"><span data-stu-id="db3f6-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db3f6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db3f6-111">Requirements</span></span>  
 <span data-ttu-id="db3f6-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db3f6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db3f6-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db3f6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db3f6-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db3f6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db3f6-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db3f6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db3f6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db3f6-116">See also</span></span>

- [<span data-ttu-id="db3f6-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="db3f6-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="db3f6-118">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="db3f6-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="db3f6-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="db3f6-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
