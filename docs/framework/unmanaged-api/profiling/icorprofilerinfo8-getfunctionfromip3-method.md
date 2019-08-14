---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f3c0a3525c87fbf39199c15a6619ff4a0d2acc42
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973703"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="6c368-102">ICorProfilerInfo8:: GetFunctionFromIP3, Metoda</span><span class="sxs-lookup"><span data-stu-id="6c368-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>
  
  <span data-ttu-id="6c368-103">Mapuje wskaźnik zarządzanej instrukcji kodu na FunctionID.</span><span class="sxs-lookup"><span data-stu-id="6c368-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="6c368-104">Ta metoda działa w przypadku metod dynamicznych i niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="6c368-104">This method works for both dynamic and non-dynamic methods.</span></span>    
  
## <a name="syntax"></a><span data-ttu-id="6c368-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c368-105">Syntax</span></span>  
  
```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c368-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c368-106">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="6c368-107">podczas Wskaźnik instrukcji w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="6c368-107">[in] The instruction pointer in managed code.</span></span>  

 `pFunctionId`  
 <span data-ttu-id="6c368-108">określoną Identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c368-108">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="6c368-109">określoną Tożsamość funkcji ponownie skompilowanej w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="6c368-109">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c368-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c368-110">Remarks</span></span>  
 <span data-ttu-id="6c368-111">Ta metoda działa w przypadku metod dynamicznych i niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="6c368-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="6c368-112">Jest to nadzbiór [GetFunctionFromIP2 —](icorprofilerinfo4-getfunctionfromip2-method.md), który działa tylko w przypadku funkcji z metadanymi.</span><span class="sxs-lookup"><span data-stu-id="6c368-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>
  

## <a name="requirements"></a><span data-ttu-id="6c368-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c368-113">Requirements</span></span>  
 <span data-ttu-id="6c368-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c368-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c368-115">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6c368-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c368-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c368-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c368-117">**.NET Framework wersje:** [! UWZGLĘDNIj[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="6c368-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c368-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c368-118">See also</span></span>
- [<span data-ttu-id="6c368-119">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c368-119">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

