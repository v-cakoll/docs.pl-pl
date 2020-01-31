---
title: ICorProfilerCallback7, interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: e61f6a104b8b9613db32ed6912395fd07c18dcff
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864820"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="6ca0e-102">ICorProfilerCallback7, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ca0e-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="6ca0e-103">[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="6ca0e-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="6ca0e-104">Podklasa elementu [ICorProfilerCallback6](icorprofilercallback6-interface.md) , która zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o aktualizacji strumienia symboli skojarzonego z modułem w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6ca0e-104">A subclass of [ICorProfilerCallback6](icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ca0e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6ca0e-105">Methods</span></span>  
  
|<span data-ttu-id="6ca0e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6ca0e-106">Method</span></span>|<span data-ttu-id="6ca0e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6ca0e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ca0e-108">ModuleInMemorySymbolsUpdated, metoda</span><span class="sxs-lookup"><span data-stu-id="6ca0e-108">ModuleInMemorySymbolsUpdated Method</span></span>](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="6ca0e-109">Powiadamia program profilujący, że jest aktualizowany strumień symboli skojarzony z modułem w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6ca0e-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ca0e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ca0e-110">Requirements</span></span>  
 <span data-ttu-id="6ca0e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ca0e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ca0e-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6ca0e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6ca0e-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ca0e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca0e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ca0e-114">See also</span></span>

- [<span data-ttu-id="6ca0e-115">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="6ca0e-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
