---
title: Interfejs ICorProfilerInfo7
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13282bec74df5e6159148aa4fbe92a84d035e044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="b8dba-102">Interfejs ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="b8dba-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="b8dba-103">[Obsługiwane w [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b8dba-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="b8dba-104">Podklasa [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) zapewnia metody do zastosowania w nowo zdefiniowane metadanych do modułu i który zapewnia dostęp do strumienia symbol w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8dba-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8dba-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b8dba-105">Methods</span></span>  
  
|<span data-ttu-id="b8dba-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b8dba-106">Method</span></span>|<span data-ttu-id="b8dba-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b8dba-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8dba-108">ApplyMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="b8dba-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="b8dba-109">Stosuje metadane wynika z nowo `IMetadataEmit::Define*` metody do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="b8dba-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="b8dba-110">GetInMemorySymbolsLength, metoda</span><span class="sxs-lookup"><span data-stu-id="b8dba-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="b8dba-111">Zwraca długość strumienia symbol w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8dba-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="b8dba-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="b8dba-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="b8dba-113">Odczytuje bajtów ze strumienia symbol w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8dba-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8dba-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8dba-114">Requirements</span></span>  
 <span data-ttu-id="b8dba-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8dba-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8dba-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b8dba-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b8dba-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8dba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8dba-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8dba-118">See Also</span></span>  
 [<span data-ttu-id="b8dba-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b8dba-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
