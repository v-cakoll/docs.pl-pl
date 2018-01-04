---
title: "IAssemblyCache — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21ebc29a6c442625f7a532f7b1e6a47e7dc4cb69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="41ac8-102">IAssemblyCache — Interfejs</span><span class="sxs-lookup"><span data-stu-id="41ac8-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="41ac8-103">Reprezentuje Globalna pamięć podręczna zestawów do użycia przez technologię fusion.</span><span class="sxs-lookup"><span data-stu-id="41ac8-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41ac8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="41ac8-104">Methods</span></span>  
  
|<span data-ttu-id="41ac8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="41ac8-105">Method</span></span>|<span data-ttu-id="41ac8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="41ac8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41ac8-107">CreateAssemblyCacheItem, metoda</span><span class="sxs-lookup"><span data-stu-id="41ac8-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="41ac8-108">Pobiera odwołanie do nowego [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="41ac8-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="41ac8-109">CreateAssemblyScavenger, metoda</span><span class="sxs-lookup"><span data-stu-id="41ac8-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="41ac8-110">Zarezerwowany do użytku wewnętrznego przez technologię fusion.</span><span class="sxs-lookup"><span data-stu-id="41ac8-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="41ac8-111">InstallAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="41ac8-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="41ac8-112">Instaluje określonego zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="41ac8-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="41ac8-113">QueryAssemblyInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="41ac8-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="41ac8-114">Pobiera żądane dane dotyczące określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="41ac8-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="41ac8-115">UninstallAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="41ac8-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="41ac8-116">Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="41ac8-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41ac8-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41ac8-117">Requirements</span></span>  
 <span data-ttu-id="41ac8-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41ac8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41ac8-119">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="41ac8-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="41ac8-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41ac8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ac8-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41ac8-121">See Also</span></span>  
 [<span data-ttu-id="41ac8-122">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="41ac8-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="41ac8-123">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="41ac8-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
