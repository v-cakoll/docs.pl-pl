---
title: ICorProfilerInfo7, interfejs
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a734bfdef89d4f8f9459f49a3ce2cee83faef9f6
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66250988"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="44e85-102">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="44e85-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="44e85-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="44e85-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="44e85-104">Podklasa klasy [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) zapewnia metody do stosowania w nowo zdefiniowane metadane do modułu i który zapewnia dostęp do strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="44e85-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44e85-105">Metody</span><span class="sxs-lookup"><span data-stu-id="44e85-105">Methods</span></span>  
  
|<span data-ttu-id="44e85-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="44e85-106">Method</span></span>|<span data-ttu-id="44e85-107">Opis</span><span class="sxs-lookup"><span data-stu-id="44e85-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44e85-108">ApplyMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="44e85-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="44e85-109">Stosuje metadane nowo zdefiniowane przez `IMetadataEmit::Define*` metody służące do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="44e85-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="44e85-110">GetInMemorySymbolsLength, metoda</span><span class="sxs-lookup"><span data-stu-id="44e85-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="44e85-111">Zwraca długość strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="44e85-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="44e85-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="44e85-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="44e85-113">Odczytuje bajtów ze strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="44e85-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44e85-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44e85-114">Requirements</span></span>  
 <span data-ttu-id="44e85-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e85-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e85-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44e85-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="44e85-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e85-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e85-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44e85-118">See also</span></span>

- [<span data-ttu-id="44e85-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="44e85-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
