---
title: ICorProfilerInfo7, interfejs
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8586031c5bcb0303a64b67ee601fe41b81ee3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786246"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="e8afa-102">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8afa-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="e8afa-103">[Obsługiwane w [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="e8afa-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="e8afa-104">Podklasa klasy [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) zapewnia metody do stosowania w nowo zdefiniowane metadane do modułu i który zapewnia dostęp do strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e8afa-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8afa-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e8afa-105">Methods</span></span>  
  
|<span data-ttu-id="e8afa-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e8afa-106">Method</span></span>|<span data-ttu-id="e8afa-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e8afa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8afa-108">ApplyMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="e8afa-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="e8afa-109">Stosuje metadane nowo zdefiniowane przez `IMetadataEmit::Define*` metody służące do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="e8afa-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="e8afa-110">GetInMemorySymbolsLength, metoda</span><span class="sxs-lookup"><span data-stu-id="e8afa-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="e8afa-111">Zwraca długość strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e8afa-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="e8afa-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="e8afa-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="e8afa-113">Odczytuje bajtów ze strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e8afa-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8afa-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8afa-114">Requirements</span></span>  
 <span data-ttu-id="e8afa-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8afa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8afa-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8afa-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8afa-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8afa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8afa-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8afa-118">See also</span></span>

- [<span data-ttu-id="e8afa-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="e8afa-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
