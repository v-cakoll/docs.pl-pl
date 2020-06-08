---
title: IHostAssemblyManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: 4e32a36a4cf751bf7c5a2c918fde0122f21b7878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501598"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="8e633-102">IHostAssemblyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8e633-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="8e633-103">Dostarcza metody, które umożliwiają hostowi określenie zestawów zestawów, które powinny być ładowane przez środowisko uruchomieniowe języka wspólnego (CLR) lub hosta.</span><span class="sxs-lookup"><span data-stu-id="8e633-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e633-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8e633-104">Methods</span></span>  
  
|<span data-ttu-id="8e633-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8e633-105">Method</span></span>|<span data-ttu-id="8e633-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8e633-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e633-107">GetAssemblyStore, metoda</span><span class="sxs-lookup"><span data-stu-id="8e633-107">GetAssemblyStore Method</span></span>](ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="8e633-108">Pobiera wskaźnik interfejsu do [IHostAssemblyStore](ihostassemblystore-interface.md) , który reprezentuje listę zestawów załadowanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="8e633-108">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="8e633-109">GetNonHostStoreAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="8e633-109">GetNonHostStoreAssemblies Method</span></span>](ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="8e633-110">Pobiera wskaźnik interfejsu do [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , który reprezentuje listę zestawów, które host oczekuje na załadowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="8e633-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e633-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e633-111">Remarks</span></span>  
 <span data-ttu-id="8e633-112">Host nie jest wymagany do implementowania `IHostAssemblyManager` ani `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="8e633-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="8e633-113">Jeśli host jest zaimplementowany `IHostAssemblyManager` , musi również implementować `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="8e633-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="8e633-114">Zapytania środowiska uruchomieniowego dla obiektu `IHostAssemblyManager` przez wywołanie [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) po zainicjowaniu z `IID` IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="8e633-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e633-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e633-115">Requirements</span></span>  
 <span data-ttu-id="8e633-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e633-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e633-117">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8e633-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e633-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8e633-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e633-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e633-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e633-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e633-120">See also</span></span>

- [<span data-ttu-id="8e633-121">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8e633-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8e633-122">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e633-122">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="8e633-123">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e633-123">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="8e633-124">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8e633-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
