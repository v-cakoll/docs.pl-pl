---
title: "ICorProfilerInfo4::GetReJITIDs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetReJITIDs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc16cd932fc2ce0cf5cb53c227081501e79ed2d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="d1332-102">ICorProfilerInfo4::GetReJITIDs — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1332-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="d1332-103">Zwraca tablicę identyfikatorów, które identyfikują wszystkie ponownie kompilowana JIT wersje określona funkcja nadal przydzielonych.</span><span class="sxs-lookup"><span data-stu-id="d1332-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="d1332-104">Dotyczy to również ponownie kompilowana JIT wersje funkcji, które później przywrócić, ale nie została jeszcze uwolnione (na przykład, gdy domeny aplikacji, która zawiera funkcję przywróconego jest nadal używane).</span><span class="sxs-lookup"><span data-stu-id="d1332-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1332-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1332-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1332-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1332-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d1332-107">[in] `FunctionID` Wystąpienia funkcji, dla którego wyliczyć wersji.</span><span class="sxs-lookup"><span data-stu-id="d1332-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="d1332-108">[in] Liczba identyfikatorów ponownie kompilowana JIT przydzielone w `reJitIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d1332-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="d1332-109">[out] Rzeczywista liczba identyfikatorów ponownie kompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="d1332-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="d1332-110">[out] Tablica przydzielone przez obiekt wywołujący, która będzie zawierać identyfikatory ponownie kompilowana JIT dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1332-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1332-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1332-111">Remarks</span></span>  
 <span data-ttu-id="d1332-112">`GetReJITIDs`Wylicza aktywne identyfikatory ponownie kompilowana JIT dla wystąpienia danej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1332-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="d1332-113">Wynika z tego samego wzorca użycia jak inne `ICorProfilerInfo` funkcje, które akceptują buforów przydzielone przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="d1332-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1332-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1332-114">Requirements</span></span>  
 <span data-ttu-id="d1332-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1332-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1332-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1332-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1332-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1332-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1332-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1332-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1332-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1332-119">See Also</span></span>  
 [<span data-ttu-id="d1332-120">ICorProfilerInfo4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d1332-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="d1332-121">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d1332-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d1332-122">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="d1332-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
