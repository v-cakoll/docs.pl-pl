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
ms.openlocfilehash: e1e114070f39e75254fc1bc0f8c1bf3e4733d5a2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703373"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="d3572-102">ICLRProbingAssemblyEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3572-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="d3572-103">Dostarcza metody, które umożliwiają hostowi pobieranie tożsamości dla zestawu przy użyciu informacji o tożsamości zestawu, które są wewnętrzne dla środowiska uruchomieniowego języka wspólnego (CLR), bez konieczności tworzenia lub zrozumienia tożsamości.</span><span class="sxs-lookup"><span data-stu-id="d3572-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3572-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d3572-104">Methods</span></span>  
  
|<span data-ttu-id="d3572-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d3572-105">Method</span></span>|<span data-ttu-id="d3572-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d3572-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3572-107">Get, metoda</span><span class="sxs-lookup"><span data-stu-id="d3572-107">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="d3572-108">Pobiera tożsamość zestawu o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="d3572-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3572-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3572-109">Remarks</span></span>  
 <span data-ttu-id="d3572-110">Metody, takie jak [ICLRAssemblyIdentityManager:: GetProbingAssembliesFromReference —](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) , zwracają `ICLRProbingAssemblyEnum` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d3572-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3572-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3572-111">Requirements</span></span>  
 <span data-ttu-id="d3572-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3572-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3572-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3572-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3572-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d3572-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3572-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3572-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3572-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3572-116">See also</span></span>

- [<span data-ttu-id="d3572-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3572-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="d3572-118">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3572-118">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d3572-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d3572-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
