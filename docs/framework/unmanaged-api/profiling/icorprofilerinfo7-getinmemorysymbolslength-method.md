---
title: Metoda ICorProfilerInfo7::GetInMemorySymbolsLength
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64289ee7fbdc440a87df6c8e506317f23e780912
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722858"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="095c1-102">Metoda ICorProfilerInfo7::GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="095c1-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="095c1-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="095c1-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="095c1-104">Zwraca długość strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="095c1-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="095c1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="095c1-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="095c1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="095c1-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="095c1-107">[in] Identyfikator modułu, zawierająca strumień w pamięci.</span><span class="sxs-lookup"><span data-stu-id="095c1-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="095c1-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="095c1-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="095c1-109">[out] Wskaźnik do `DWORD` wartość, gdy metoda zwróci wartość, zawiera długość strumienia w bajtach.</span><span class="sxs-lookup"><span data-stu-id="095c1-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="095c1-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="095c1-110">Return Value</span></span>  
 <span data-ttu-id="095c1-111">Metoda ta zwraca `S_OK` Jeśli długość strumienia pamięci można ustalić, nawet jeśli ma wartość zero (0).</span><span class="sxs-lookup"><span data-stu-id="095c1-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="095c1-112">Metoda ta zwraca `CORPROF_E_MODULE_IS_DYNAMIC` Jeśli metoda został utworzony przy użyciu <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="095c1-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="095c1-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="095c1-113">Remarks</span></span>  
 <span data-ttu-id="095c1-114">Jeśli moduł zawiera symbole w pamięci, długość strumienia jest umieszczany w `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="095c1-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="095c1-115">Jeśli moduł nie ma symboli w pamięci, `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="095c1-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="095c1-116">Bieżąca implementacja nie obsługuje Reflection.Emit.</span><span class="sxs-lookup"><span data-stu-id="095c1-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="095c1-117">Jeśli moduł został utworzony przy użyciu Reflection.Emit, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="095c1-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="095c1-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="095c1-118">Requirements</span></span>  
 <span data-ttu-id="095c1-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="095c1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="095c1-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="095c1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="095c1-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="095c1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="095c1-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="095c1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="095c1-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="095c1-123">See also</span></span>
- [<span data-ttu-id="095c1-124">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="095c1-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
