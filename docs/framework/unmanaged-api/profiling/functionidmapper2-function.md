---
title: FunctionIDMapper2 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92285d6aef41595fd4729aa82a827c3efc09b03f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451896"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="fc482-102">FunctionIDMapper2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="fc482-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="fc482-103">Powiadamia profilera, że danym identyfikatorem funkcji mogą być mapowane ponownie do alternatywny identyfikator ma być używany w [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), lub[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) wywołań zwrotnych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="fc482-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="fc482-104">`FunctionIDMapper2` Umożliwia również profilera wskazać, czy chce odbierać wywołań zwrotnych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="fc482-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc482-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc482-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc482-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc482-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="fc482-107">[in] Identyfikator funkcji można zamapować go ponownie.</span><span class="sxs-lookup"><span data-stu-id="fc482-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="fc482-108">[in] Wskaźnik do danych, który służy do odróżniania między środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="fc482-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="fc482-109">[out] Wskaźnik do wartości, która ustawia profilera `true` jeśli chce otrzymywać `FunctionEnter3`, `FunctionLeave3`, i `FunctionTailcall3`, lub `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, i `FunctionTailcall3WithInfo` wywołania zwrotne; w przeciwnym razie ustawia tę wartość na `false`.</span><span class="sxs-lookup"><span data-stu-id="fc482-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc482-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc482-110">Return Value</span></span>  
 <span data-ttu-id="fc482-111">Profiler zwraca wartość używaną przez aparat wykonywania jako identyfikator alternatywny funkcji.</span><span class="sxs-lookup"><span data-stu-id="fc482-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="fc482-112">Wartość zwrotna nie może mieć wartości null chyba że `false` jest zwracany w `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="fc482-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="fc482-113">W przeciwnym razie zwrócenie wartości null powoduje nieoczekiwane wyniki, w tym prawdopodobnie zatrzymywanie procesu.</span><span class="sxs-lookup"><span data-stu-id="fc482-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc482-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc482-114">Remarks</span></span>  
 <span data-ttu-id="fc482-115">Ta metoda jest rozszerzeniem [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkcji z parametrem dodatkowych, który jest używany do przekazywania danych klienta.</span><span class="sxs-lookup"><span data-stu-id="fc482-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="fc482-116">Dane klienta są używane do odróżniania między środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="fc482-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc482-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc482-117">Requirements</span></span>  
 <span data-ttu-id="fc482-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc482-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc482-119">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="fc482-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="fc482-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc482-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc482-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc482-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc482-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc482-122">See Also</span></span>  
 [<span data-ttu-id="fc482-123">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="fc482-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="fc482-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="fc482-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="fc482-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="fc482-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="fc482-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="fc482-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="fc482-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="fc482-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="fc482-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fc482-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="fc482-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fc482-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="fc482-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fc482-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="fc482-131">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="fc482-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
