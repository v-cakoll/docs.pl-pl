---
title: ICorProfilerInfo7, interfejs
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861752"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="97f84-102">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="97f84-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="97f84-103">[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="97f84-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="97f84-104">Podklasa elementu [ICorProfilerInfo6](icorprofilerinfo6-interface.md) , która zapewnia metodę zastosowania nowo zdefiniowanych metadanych do modułu i zapewnia dostęp do strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="97f84-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97f84-105">Metody</span><span class="sxs-lookup"><span data-stu-id="97f84-105">Methods</span></span>  
  
|<span data-ttu-id="97f84-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="97f84-106">Method</span></span>|<span data-ttu-id="97f84-107">Opis</span><span class="sxs-lookup"><span data-stu-id="97f84-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97f84-108">ApplyMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="97f84-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="97f84-109">Stosuje metadane nowo zdefiniowane przez metody `IMetadataEmit::Define*` do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="97f84-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="97f84-110">GetInMemorySymbolsLength, metoda</span><span class="sxs-lookup"><span data-stu-id="97f84-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="97f84-111">Zwraca długość strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="97f84-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="97f84-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="97f84-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="97f84-113">Odczytuje bajty z strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="97f84-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97f84-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97f84-114">Requirements</span></span>  
 <span data-ttu-id="97f84-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97f84-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97f84-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="97f84-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97f84-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97f84-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f84-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97f84-118">See also</span></span>

- [<span data-ttu-id="97f84-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="97f84-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
