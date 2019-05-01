---
title: ICorProfilerInfo4::GetFunctionFromIP2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18099e6e658391d6dae7a666cd0cebefa5859b1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971551"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="98e46-102">ICorProfilerInfo4::GetFunctionFromIP2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="98e46-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="98e46-103">Mapuje wskaźnik instrukcji kodu zarządzanego do wersji ponownie skompilowana JIT funkcji.</span><span class="sxs-lookup"><span data-stu-id="98e46-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="98e46-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98e46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98e46-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="98e46-106">[in] Wskaźnik instrukcji w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="98e46-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="98e46-107">[out] Identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="98e46-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="98e46-108">[out] Tożsamość ponownie skompilowana JIT wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="98e46-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98e46-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98e46-109">Remarks</span></span>  
 <span data-ttu-id="98e46-110">`GetFunctionFromIP2` jest podobny do `GetFunctionFromIP`, chyba że otrzymuje identyfikator ponownie skompilowana JIT, zamiast Identyfikatora funkcji, funkcji, która zawiera określony adres IP.</span><span class="sxs-lookup"><span data-stu-id="98e46-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98e46-111">`GetFunctionFromIP2` Możesz wyzwolić wyrzucania elementów bezużytecznych, natomiast `GetFunctionFromIP` nie będzie.</span><span class="sxs-lookup"><span data-stu-id="98e46-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="98e46-112">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="98e46-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e46-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98e46-113">Requirements</span></span>  
 <span data-ttu-id="98e46-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e46-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e46-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="98e46-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98e46-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98e46-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98e46-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e46-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e46-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98e46-118">See also</span></span>

- [<span data-ttu-id="98e46-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="98e46-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
