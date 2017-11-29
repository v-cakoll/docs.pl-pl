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
ms.openlocfilehash: 6244e6c3b0cc88c50cda050a480f5af5b3996b47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="b27c4-102">IAssemblyCache — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b27c4-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="b27c4-103">Reprezentuje Globalna pamięć podręczna zestawów do użycia przez technologię fusion.</span><span class="sxs-lookup"><span data-stu-id="b27c4-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b27c4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b27c4-104">Methods</span></span>  
  
|<span data-ttu-id="b27c4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b27c4-105">Method</span></span>|<span data-ttu-id="b27c4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b27c4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b27c4-107">CreateAssemblyCacheItem — metoda</span><span class="sxs-lookup"><span data-stu-id="b27c4-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="b27c4-108">Pobiera odwołanie do nowego [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b27c4-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="b27c4-109">CreateAssemblyScavenger — metoda</span><span class="sxs-lookup"><span data-stu-id="b27c4-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="b27c4-110">Zarezerwowany do użytku wewnętrznego przez technologię fusion.</span><span class="sxs-lookup"><span data-stu-id="b27c4-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="b27c4-111">InstallAssembly — metoda</span><span class="sxs-lookup"><span data-stu-id="b27c4-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="b27c4-112">Instaluje określonego zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b27c4-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="b27c4-113">QueryAssemblyInfo — metoda</span><span class="sxs-lookup"><span data-stu-id="b27c4-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="b27c4-114">Pobiera żądane dane dotyczące określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b27c4-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="b27c4-115">UninstallAssembly — metoda</span><span class="sxs-lookup"><span data-stu-id="b27c4-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="b27c4-116">Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b27c4-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b27c4-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b27c4-117">Requirements</span></span>  
 <span data-ttu-id="b27c4-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b27c4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b27c4-119">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b27c4-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b27c4-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b27c4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b27c4-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b27c4-121">See Also</span></span>  
 [<span data-ttu-id="b27c4-122">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="b27c4-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="b27c4-123">Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="b27c4-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
