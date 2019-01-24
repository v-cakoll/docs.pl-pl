---
title: ICorProfilerInfo4::GetReJITIDs — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6cb3a2235325533d5bd943a530a0a8e5b77100e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519947"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="0d922-102">ICorProfilerInfo4::GetReJITIDs — Metoda</span><span class="sxs-lookup"><span data-stu-id="0d922-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="0d922-103">Zwraca tablicę identyfikatorów, które identyfikują wszystkie ponownie skompilowana JIT wersje określonej funkcji, które nadal są przydzielane.</span><span class="sxs-lookup"><span data-stu-id="0d922-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="0d922-104">Obejmuje to ponownie skompilowana JIT wersje funkcji, które następnie przywrócona, ale nie zostały jeszcze zwolnione (na przykład, gdy domeny aplikacji, która zawiera przywróconym funkcja jest nadal w użyciu).</span><span class="sxs-lookup"><span data-stu-id="0d922-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d922-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d922-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d922-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d922-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0d922-107">[in] `FunctionID` Wystąpienia funkcji, do których chcesz wyliczyć wersji.</span><span class="sxs-lookup"><span data-stu-id="0d922-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="0d922-108">[in] Liczba identyfikatorów ponownie skompilowana JIT, przydzielone w `reJitIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0d922-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="0d922-109">[out] Rzeczywista liczba identyfikatorów ponownie skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="0d922-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="0d922-110">[out] Tablica przydzielana przez obiekt wywołujący, który będzie zawierać identyfikatory ponownie skompilowana JIT dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0d922-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d922-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d922-111">Remarks</span></span>  
 <span data-ttu-id="0d922-112">`GetReJITIDs` Wylicza aktywne identyfikatory ponownie skompilowana JIT dla wystąpienia danej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0d922-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="0d922-113">Wynika z tego samego wzorca użycia, jak inne `ICorProfilerInfo` funkcje, które akceptują bufory przypisane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0d922-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d922-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d922-114">Requirements</span></span>  
 <span data-ttu-id="0d922-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d922-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d922-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d922-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d922-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d922-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d922-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d922-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d922-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d922-119">See also</span></span>
- [<span data-ttu-id="0d922-120">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d922-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="0d922-121">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="0d922-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="0d922-122">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="0d922-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
