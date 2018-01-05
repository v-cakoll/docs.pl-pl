---
title: "ICorProfilerInfo7::GetInMemorySymbolsLength — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type: COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c1299429e9173069c5a39fe4a2b82d1db5938f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="99652-102">ICorProfilerInfo7::GetInMemorySymbolsLength — metoda</span><span class="sxs-lookup"><span data-stu-id="99652-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="99652-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="99652-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="99652-104">Zwraca długość strumienia symbol w pamięci.</span><span class="sxs-lookup"><span data-stu-id="99652-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99652-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="99652-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99652-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="99652-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="99652-107">[in] Identyfikator modułu zawierającego strumienia w pamięci.</span><span class="sxs-lookup"><span data-stu-id="99652-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="99652-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="99652-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="99652-109">[out] Wskaźnik do `DWORD` wartość, gdy metoda zwróci wartość, zawiera długość strumienia w bajtach.</span><span class="sxs-lookup"><span data-stu-id="99652-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99652-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="99652-110">Return Value</span></span>  
 <span data-ttu-id="99652-111">Metoda zwraca `S_OK` Jeśli długość strumienia pamięci można ustalić, nawet jeśli jest ona zero (0).</span><span class="sxs-lookup"><span data-stu-id="99652-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="99652-112">Metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC` Jeśli metoda została utworzona przy użyciu <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99652-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99652-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99652-113">Remarks</span></span>  
 <span data-ttu-id="99652-114">Jeśli moduł zawiera symbole w pamięci, długość strumienia jest umieszczany w `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="99652-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="99652-115">Jeśli moduł nie ma symboli w pamięci `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="99652-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99652-116">Bieżąca implementacja nie obsługuje Reflection.Emit.</span><span class="sxs-lookup"><span data-stu-id="99652-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="99652-117">Jeśli moduł został utworzony przy użyciu Reflection.Emit, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="99652-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99652-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99652-118">Requirements</span></span>  
 <span data-ttu-id="99652-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99652-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99652-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="99652-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="99652-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99652-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99652-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99652-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99652-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99652-123">See Also</span></span>  
 [<span data-ttu-id="99652-124">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="99652-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
