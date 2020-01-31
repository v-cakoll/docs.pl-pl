---
title: 'ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated, Metoda'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: 6fbb86fc63a26599ae83c81817dbcb9abfb88cc8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864692"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="a3359-102">ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated, Metoda</span><span class="sxs-lookup"><span data-stu-id="a3359-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="a3359-103">[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="a3359-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="a3359-104">Powiadamia profiler za każdym razem, gdy zostanie zaktualizowany strumień symboli skojarzony z modułem w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a3359-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3359-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3359-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3359-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3359-106">Parameters</span></span>  
 <span data-ttu-id="a3359-107">[in] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="a3359-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="a3359-108">Identyfikator modułu w pamięci, którego strumień symboli został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="a3359-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3359-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3359-109">Remarks</span></span>  
 <span data-ttu-id="a3359-110">To wywołanie zwrotne jest kontrolowane przez ustawienie flagi maski zdarzeń [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) podczas wywoływania metody [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a3359-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3359-111">To zdarzenie nie jest obecnie wywoływane dla symboli niejawnie utworzonych lub zmodyfikowanych za pośrednictwem <xref:System.Reflection.Emit> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="a3359-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="a3359-112">Nawet w przypadku podania symboli przede wszystkim w wywołaniu jednego z przeciążeń zarządzanych metod <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, które zawierają `rawSymbolStore` argument, aby określić symbole dla zestawu, środowisko uruchomieniowe może nie skojarzyć danych symbolicznych z modułem do momentu wystąpienia wywołania zwrotnego [ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a3359-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="a3359-113">To zdarzenie umożliwia późniejsze zbieranie symboli dla takich modułów.</span><span class="sxs-lookup"><span data-stu-id="a3359-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3359-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3359-114">Requirements</span></span>  
 <span data-ttu-id="a3359-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3359-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3359-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a3359-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3359-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a3359-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3359-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3359-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3359-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3359-119">See also</span></span>

- [<span data-ttu-id="a3359-120">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="a3359-120">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="a3359-121">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="a3359-121">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="a3359-122">ICorProfilerCallback7, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3359-122">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)
