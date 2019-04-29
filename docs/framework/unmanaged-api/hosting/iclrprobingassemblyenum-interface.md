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
ms.openlocfilehash: 118345f246de3d7ee68d51cf37e8cdea9de1fdba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638531"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="2f073-102">ICLRProbingAssemblyEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2f073-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="2f073-103">Udostępnia metody umożliwiające hosta można pobrać badania tożsamości zestawu przy użyciu informacji o tożsamości zestawu, jest wewnętrzny środowisko uruchomieniowe języka wspólnego (CLR), bez konieczności tworzenia lub zrozumieć tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="2f073-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f073-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2f073-104">Methods</span></span>  
  
|<span data-ttu-id="2f073-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2f073-105">Method</span></span>|<span data-ttu-id="2f073-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2f073-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f073-107">Get, metoda</span><span class="sxs-lookup"><span data-stu-id="2f073-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="2f073-108">Pobiera tożsamość zestawu pod określonym indeksem.</span><span class="sxs-lookup"><span data-stu-id="2f073-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f073-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f073-109">Remarks</span></span>  
 <span data-ttu-id="2f073-110">Metody takie jak [iclrassemblyidentitymanager::getprobingassembliesfromreference —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) zwracają `ICLRProbingAssemblyEnum` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2f073-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f073-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f073-111">Requirements</span></span>  
 <span data-ttu-id="2f073-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f073-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f073-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2f073-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f073-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2f073-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f073-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f073-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f073-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f073-116">See also</span></span>

- [<span data-ttu-id="2f073-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f073-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="2f073-118">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f073-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2f073-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2f073-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
