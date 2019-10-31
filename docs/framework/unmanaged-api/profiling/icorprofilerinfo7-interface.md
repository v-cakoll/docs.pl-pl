---
title: ICorProfilerInfo7, interfejs
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4c7e94ffa60bcfaead009e1a8baa9b54b2e8ab7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125051"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="6f1ad-102">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f1ad-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="6f1ad-103">[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="6f1ad-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="6f1ad-104">Podklasa elementu [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) , która zapewnia metodę zastosowania nowo zdefiniowanych metadanych do modułu i zapewnia dostęp do strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f1ad-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f1ad-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6f1ad-105">Methods</span></span>  
  
|<span data-ttu-id="6f1ad-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6f1ad-106">Method</span></span>|<span data-ttu-id="6f1ad-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6f1ad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f1ad-108">ApplyMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="6f1ad-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="6f1ad-109">Stosuje metadane nowo zdefiniowane przez metody `IMetadataEmit::Define*` do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="6f1ad-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="6f1ad-110">GetInMemorySymbolsLength, metoda</span><span class="sxs-lookup"><span data-stu-id="6f1ad-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="6f1ad-111">Zwraca długość strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f1ad-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="6f1ad-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="6f1ad-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="6f1ad-113">Odczytuje bajty z strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6f1ad-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f1ad-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f1ad-114">Requirements</span></span>  
 <span data-ttu-id="6f1ad-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f1ad-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f1ad-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6f1ad-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f1ad-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f1ad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1ad-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f1ad-118">See also</span></span>

- [<span data-ttu-id="6f1ad-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="6f1ad-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
