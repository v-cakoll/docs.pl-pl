---
title: Interfejs ICorProfilerCallback7
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8eb370e4f16212c536c252661163b7eca6f74d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="f5636-102">Interfejs ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="f5636-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="f5636-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="f5636-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="f5636-104">Podklasa [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) zapewnia metody wywołania zwrotnego, która środowisko uruchomieniowe języka wspólnego używa do powiadamiania profilera zaktualizowaniu strumienia symbol skojarzone z modułu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f5636-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5636-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f5636-105">Methods</span></span>  
  
|<span data-ttu-id="f5636-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f5636-106">Method</span></span>|<span data-ttu-id="f5636-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f5636-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5636-108">ModuleInMemorySymbolsUpdated — metoda</span><span class="sxs-lookup"><span data-stu-id="f5636-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="f5636-109">Powiadamia profilera zaktualizowaniu strumienia symbol skojarzone z modułu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f5636-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5636-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5636-110">Requirements</span></span>  
 <span data-ttu-id="f5636-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5636-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5636-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f5636-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5636-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5636-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5636-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5636-114">See Also</span></span>  
 [<span data-ttu-id="f5636-115">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f5636-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
