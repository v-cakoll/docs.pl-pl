---
title: ICorProfilerInfo7, interfejs
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8586031c5bcb0303a64b67ee601fe41b81ee3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134865"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="d846f-102">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="d846f-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="d846f-103">[Obsługiwane w [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="d846f-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="d846f-104">Podklasa klasy [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) zapewnia metody do stosowania w nowo zdefiniowane metadane do modułu i który zapewnia dostęp do strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d846f-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d846f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d846f-105">Methods</span></span>  
  
|<span data-ttu-id="d846f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d846f-106">Method</span></span>|<span data-ttu-id="d846f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d846f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d846f-108">ApplyMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="d846f-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="d846f-109">Stosuje metadane nowo zdefiniowane przez `IMetadataEmit::Define*` metody służące do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="d846f-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="d846f-110">GetInMemorySymbolsLength, metoda</span><span class="sxs-lookup"><span data-stu-id="d846f-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="d846f-111">Zwraca długość strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d846f-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="d846f-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="d846f-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="d846f-113">Odczytuje bajtów ze strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d846f-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d846f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d846f-114">Requirements</span></span>  
 <span data-ttu-id="d846f-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d846f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d846f-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d846f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="d846f-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d846f-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d846f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d846f-118">See also</span></span>

- [<span data-ttu-id="d846f-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d846f-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
