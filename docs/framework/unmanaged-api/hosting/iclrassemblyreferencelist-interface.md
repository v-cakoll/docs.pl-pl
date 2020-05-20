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
ms.openlocfilehash: f1aa40ef868bf6ff7730e01ab66a6fec58af1196
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615881"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="7fecb-102">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7fecb-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="7fecb-103">Zarządza listą zestawów, które są ładowane przez środowisko uruchomieniowe języka wspólnego (CLR), a nie przez hosta.</span><span class="sxs-lookup"><span data-stu-id="7fecb-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fecb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7fecb-104">Methods</span></span>  
  
|<span data-ttu-id="7fecb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7fecb-105">Method</span></span>|<span data-ttu-id="7fecb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7fecb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fecb-107">IsAssemblyReferenceInList, metoda</span><span class="sxs-lookup"><span data-stu-id="7fecb-107">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="7fecb-108">Pobiera wartość wskazującą, czy dostarczony wskaźnik odwołuje się do zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="7fecb-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="7fecb-109">IsStringAssemblyReferenceInList, metoda</span><span class="sxs-lookup"><span data-stu-id="7fecb-109">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="7fecb-110">Pobiera wartość wskazującą, czy podana nazwa jest zgodna z nazwą zestawu znajdującego się na liście.</span><span class="sxs-lookup"><span data-stu-id="7fecb-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fecb-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fecb-111">Remarks</span></span>  
 <span data-ttu-id="7fecb-112">Wywołaj metodę [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList —](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) , aby uzyskać wskaźnik do wystąpienia `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="7fecb-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fecb-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7fecb-113">Requirements</span></span>  
 <span data-ttu-id="7fecb-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fecb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fecb-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7fecb-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fecb-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7fecb-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fecb-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fecb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fecb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fecb-118">See also</span></span>

- [<span data-ttu-id="7fecb-119">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7fecb-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="7fecb-120">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="7fecb-120">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="7fecb-121">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7fecb-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
