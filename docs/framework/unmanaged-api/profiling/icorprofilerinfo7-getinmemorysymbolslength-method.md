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
ms.openlocfilehash: 34da00bdc33a836e5f459e6e4314f252e1e39e9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="ab7a6-102">ICorProfilerInfo7::GetInMemorySymbolsLength — metoda</span><span class="sxs-lookup"><span data-stu-id="ab7a6-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="ab7a6-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="ab7a6-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="ab7a6-104">Zwraca długość strumienia symbol w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ab7a6-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab7a6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab7a6-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab7a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab7a6-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ab7a6-107">[in] Identyfikator modułu zawierającego strumienia w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ab7a6-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="ab7a6-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="ab7a6-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="ab7a6-109">[out] Wskaźnik do `DWORD` wartość, gdy metoda zwróci wartość, zawiera długość strumienia w bajtach.</span><span class="sxs-lookup"><span data-stu-id="ab7a6-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab7a6-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ab7a6-110">Return Value</span></span>  
 <span data-ttu-id="ab7a6-111">Metoda zwraca `S_OK` Jeśli długość strumienia pamięci można ustalić, nawet jeśli jest ona zero (0).</span><span class="sxs-lookup"><span data-stu-id="ab7a6-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="ab7a6-112">Metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC` Jeśli metoda została utworzona przy użyciu <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ab7a6-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab7a6-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab7a6-113">Remarks</span></span>  
 <span data-ttu-id="ab7a6-114">Jeśli moduł zawiera symbole w pamięci, długość strumienia jest umieszczany w `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="ab7a6-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="ab7a6-115">Jeśli moduł nie ma symboli w pamięci `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="ab7a6-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab7a6-116">Bieżąca implementacja nie obsługuje Reflection.Emit.</span><span class="sxs-lookup"><span data-stu-id="ab7a6-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="ab7a6-117">Jeśli moduł został utworzony przy użyciu Reflection.Emit, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="ab7a6-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab7a6-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab7a6-118">Requirements</span></span>  
 <span data-ttu-id="ab7a6-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab7a6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab7a6-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab7a6-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab7a6-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab7a6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab7a6-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab7a6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab7a6-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab7a6-123">See Also</span></span>  
 [<span data-ttu-id="ab7a6-124">Interfejs ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="ab7a6-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
