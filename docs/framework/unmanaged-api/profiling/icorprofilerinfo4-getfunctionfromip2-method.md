---
title: "ICorProfilerInfo4::GetFunctionFromIP2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetFunctionFromIP2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f354bdc198a8060c7241a2b9bdb472bee5ed7b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="a6957-102">ICorProfilerInfo4::GetFunctionFromIP2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6957-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="a6957-103">Mapuje wskaźnik instrukcji kodu zarządzanego do wersji ponownie kompilowana JIT funkcji.</span><span class="sxs-lookup"><span data-stu-id="a6957-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6957-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6957-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6957-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6957-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="a6957-106">[in] Wskaźnik instrukcji w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="a6957-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="a6957-107">[out] Identyfikatorem funkcji.</span><span class="sxs-lookup"><span data-stu-id="a6957-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="a6957-108">[out] Tożsamość wersji ponownie kompilowana JIT funkcji.</span><span class="sxs-lookup"><span data-stu-id="a6957-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6957-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6957-109">Remarks</span></span>  
 <span data-ttu-id="a6957-110">`GetFunctionFromIP2`przypomina `GetFunctionFromIP`, ale pobiera identyfikator ponownie kompilowana JIT zamiast Identyfikatora funkcji funkcji, która zawiera określony adres IP.</span><span class="sxs-lookup"><span data-stu-id="a6957-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6957-111">`GetFunctionFromIP2`może wyzwolić wyrzucania elementów bezużytecznych, podczas gdy `GetFunctionFromIP` nie.</span><span class="sxs-lookup"><span data-stu-id="a6957-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="a6957-112">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="a6957-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6957-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6957-113">Requirements</span></span>  
 <span data-ttu-id="a6957-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6957-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6957-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6957-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6957-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6957-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6957-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6957-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6957-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6957-118">See Also</span></span>  
 [<span data-ttu-id="a6957-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6957-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
