---
title: Interfejs ICorProfilerInfo7
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79a722cd3318def36c20a49c1567c6f0d4989d39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="b0c32-102">Interfejs ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="b0c32-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="b0c32-103">[Obsługiwane w [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b0c32-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="b0c32-104">Podklasa [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) zapewnia metody do zastosowania w nowo zdefiniowane metadanych do modułu i który zapewnia dostęp do strumienia symbol w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b0c32-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0c32-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b0c32-105">Methods</span></span>  
  
|<span data-ttu-id="b0c32-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0c32-106">Method</span></span>|<span data-ttu-id="b0c32-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b0c32-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0c32-108">ApplyMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c32-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="b0c32-109">Stosuje metadane wynika z nowo `IMetadataEmit::Define*` metody do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="b0c32-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="b0c32-110">GetInMemorySymbolsLength, metoda</span><span class="sxs-lookup"><span data-stu-id="b0c32-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="b0c32-111">Zwraca długość strumienia symbol w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b0c32-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="b0c32-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="b0c32-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="b0c32-113">Odczytuje bajtów ze strumienia symbol w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b0c32-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0c32-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0c32-114">Requirements</span></span>  
 <span data-ttu-id="b0c32-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0c32-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0c32-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b0c32-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0c32-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0c32-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c32-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0c32-118">See Also</span></span>  
 [<span data-ttu-id="b0c32-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b0c32-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
