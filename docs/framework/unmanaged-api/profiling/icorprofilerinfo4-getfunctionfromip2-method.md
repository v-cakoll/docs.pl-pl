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
ms.openlocfilehash: ea66474e809b3813faceef79a69dd8a639a72a3b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502798"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="7230b-102">ICorProfilerInfo4::GetFunctionFromIP2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="7230b-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="7230b-103">Mapuje wskaźnik zarządzanej instrukcji kodu do wersji funkcji ponownie skompilowanej przez JIT.</span><span class="sxs-lookup"><span data-stu-id="7230b-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7230b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7230b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7230b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7230b-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="7230b-106">podczas Wskaźnik instrukcji w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="7230b-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="7230b-107">określoną Identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="7230b-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="7230b-108">określoną Tożsamość funkcji ponownie skompilowanej w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="7230b-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7230b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7230b-109">Remarks</span></span>  
 <span data-ttu-id="7230b-110">`GetFunctionFromIP2`jest podobny do `GetFunctionFromIP` , z tą różnicą, że pobiera identyfikator JIT-ponownie skompilowany zamiast identyfikatora funkcji funkcji, która zawiera określony adres IP.</span><span class="sxs-lookup"><span data-stu-id="7230b-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7230b-111">`GetFunctionFromIP2`może wyzwolić wyrzucanie elementów bezużytecznych, natomiast `GetFunctionFromIP` nie będzie.</span><span class="sxs-lookup"><span data-stu-id="7230b-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="7230b-112">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="7230b-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7230b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7230b-113">Requirements</span></span>  
 <span data-ttu-id="7230b-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7230b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7230b-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7230b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7230b-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7230b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7230b-117">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7230b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7230b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7230b-118">See also</span></span>

- [<span data-ttu-id="7230b-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7230b-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
