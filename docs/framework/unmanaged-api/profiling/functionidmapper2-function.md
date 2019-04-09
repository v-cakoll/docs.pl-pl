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
ms.openlocfilehash: 1a236dcae29d00afe3b72dce8f81d657fb4fac28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082506"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="8d348-102">FunctionIDMapper2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8d348-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="8d348-103">Powiadamia program profilujący, że identyfikator danej funkcji może być ponownie mapowany do alternatywnego Identyfikatora do użycia w [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), lub[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) wywołań zwrotnych tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8d348-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> `FunctionIDMapper2` <span data-ttu-id="8d348-104">Umożliwia także profilującemu wskazanie, czy chce odbierać wywołania zwrotne do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8d348-104">also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d348-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d348-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d348-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d348-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="8d348-107">[in] Identyfikator funkcji ma być ponownie mapowany.</span><span class="sxs-lookup"><span data-stu-id="8d348-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="8d348-108">[in] Wskaźnik do danych, który służy do rozróżniać wśród modułów wykonawczych.</span><span class="sxs-lookup"><span data-stu-id="8d348-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="8d348-109">[out] Wskaźnik do wartości, która ustawia program profilujący `true` jeśli chce otrzymać `FunctionEnter3`, `FunctionLeave3`, i `FunctionTailcall3`, lub `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, i `FunctionTailcall3WithInfo` wywołań zwrotnych; w przeciwnym wypadku ustawia tę wartość, aby `false`.</span><span class="sxs-lookup"><span data-stu-id="8d348-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d348-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8d348-110">Return Value</span></span>  
 <span data-ttu-id="8d348-111">Program profilujący zwraca wartość, której używa silnik wykonawczy jako identyfikatora alternatywnej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8d348-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="8d348-112">Zwracana wartość nie może mieć wartości null Jeśli nie `false` jest zwracany w `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="8d348-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="8d348-113">W przeciwnym razie zwracana wartość null produkuje nieoczekiwanych rezultatów, w tym ewentualnie powstrzymanie procesu.</span><span class="sxs-lookup"><span data-stu-id="8d348-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d348-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d348-114">Remarks</span></span>  
 <span data-ttu-id="8d348-115">Ta metoda jest rozszerzeniem [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkcję o dodatkowy parametr, który jest używany do przekazania danych klienta.</span><span class="sxs-lookup"><span data-stu-id="8d348-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="8d348-116">Dane klienta są używane do rozróżniać wśród modułów wykonawczych.</span><span class="sxs-lookup"><span data-stu-id="8d348-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d348-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d348-117">Requirements</span></span>  
 <span data-ttu-id="8d348-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d348-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d348-119">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="8d348-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8d348-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d348-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8d348-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8d348-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8d348-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d348-122">See also</span></span>

- [<span data-ttu-id="8d348-123">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="8d348-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="8d348-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="8d348-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="8d348-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="8d348-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="8d348-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="8d348-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="8d348-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="8d348-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="8d348-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="8d348-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="8d348-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="8d348-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="8d348-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="8d348-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="8d348-131">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="8d348-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
