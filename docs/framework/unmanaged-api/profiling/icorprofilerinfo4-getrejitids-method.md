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
ms.openlocfilehash: 805ceb60d2ac122df2382656b95b7bf5e7509bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855940"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="d1ef2-102">ICorProfilerInfo4::GetReJITIDs — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1ef2-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="d1ef2-103">Zwraca tablicę identyfikatorów, które identyfikują wszystkie wersje JIT-ponownie skompilowane określonej funkcji, które są nadal przydzieleni.</span><span class="sxs-lookup"><span data-stu-id="d1ef2-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="d1ef2-104">Obejmuje to ponowne skompilowane przez JIT wersje funkcji, które zostały później przywrócone, ale nie zostały jeszcze zwolnione (na przykład wtedy, gdy domena aplikacji zawierająca przywróconą funkcję jest nadal w użyciu).</span><span class="sxs-lookup"><span data-stu-id="d1ef2-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ef2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1ef2-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1ef2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1ef2-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d1ef2-107">podczas `FunctionID` Wystąpienia funkcji, dla którego mają zostać wyliczone wersje.</span><span class="sxs-lookup"><span data-stu-id="d1ef2-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="d1ef2-108">podczas Liczba identyfikatorów ponownych kompilacji JIT przypisywanych w `reJitIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d1ef2-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="d1ef2-109">określoną Rzeczywista liczba identyfikatorów ponownych kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="d1ef2-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="d1ef2-110">określoną Tablica przypisana przez obiekt wywołujący, która będzie zawierać identyfikatory ponownie skompilowane JIT dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1ef2-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1ef2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1ef2-111">Remarks</span></span>  
 <span data-ttu-id="d1ef2-112">`GetReJITIDs`wylicza aktywne, ponownie skompilowane identyfikatory JIT dla danego wystąpienia funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1ef2-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="d1ef2-113">Jest on zgodny z tym samym wzorcem `ICorProfilerInfo` użycia, co inne funkcje, które akceptują bufory przydzieloną przez proces wywołujący.</span><span class="sxs-lookup"><span data-stu-id="d1ef2-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1ef2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1ef2-114">Requirements</span></span>  
 <span data-ttu-id="d1ef2-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1ef2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1ef2-116">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d1ef2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1ef2-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1ef2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1ef2-118">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1ef2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ef2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1ef2-119">See also</span></span>

- [<span data-ttu-id="d1ef2-120">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1ef2-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="d1ef2-121">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d1ef2-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d1ef2-122">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="d1ef2-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
