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
ms.openlocfilehash: af0ef412395394bb660ae6ed64fb154caef41655
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866921"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="aa8df-102">FunctionIDMapper2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="aa8df-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="aa8df-103">Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)i [FunctionTailcall3](functiontailcall3-function.md), lub[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)i [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa8df-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="aa8df-104">`FunctionIDMapper2` również umożliwia profilerowi określenie, czy chce otrzymywać wywołania zwrotne dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa8df-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa8df-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa8df-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa8df-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa8df-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="aa8df-107">\[] identyfikator funkcji, która ma zostać ponownie zmapowana.</span><span class="sxs-lookup"><span data-stu-id="aa8df-107">\[in] The function identifier to be remapped.</span></span>

- `clientData`

  <span data-ttu-id="aa8df-108">\[w] wskaźnik do danych, który jest używany do rozróżnienia między środowiskami uruchomieniowymi.</span><span class="sxs-lookup"><span data-stu-id="aa8df-108">\[in] A pointer to data that is used to disambiguate among runtimes.</span></span>

- `pbHookFunction`

  <span data-ttu-id="aa8df-109">\[out] wskaźnik do wartości, która jest ustawiana przez profiler `true`, jeśli chce otrzymywać `FunctionEnter3`, `FunctionLeave3`i `FunctionTailcall3`, lub `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`i `FunctionTailcall3WithInfo` wywołania zwrotne; w przeciwnym razie ustawia tę wartość na `false`.</span><span class="sxs-lookup"><span data-stu-id="aa8df-109">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="aa8df-110">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="aa8df-110">Return Value</span></span>  
 <span data-ttu-id="aa8df-111">Profiler zwraca wartość, którą aparat wykonywania używa jako alternatywnego identyfikatora funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa8df-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="aa8df-112">Zwracana wartość nie może mieć wartości null, chyba że `false` jest zwracana w `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="aa8df-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="aa8df-113">W przeciwnym razie wartość zwracana null da nieprzewidywalne wyniki, w tym prawdopodobnie zatrzymanie procesu.</span><span class="sxs-lookup"><span data-stu-id="aa8df-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa8df-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa8df-114">Remarks</span></span>  
 <span data-ttu-id="aa8df-115">Ta metoda rozszerza funkcję [FunctionIDMapper](functionidmapper-function.md) z dodatkowym parametrem, który służy do przekazywania danych klienta.</span><span class="sxs-lookup"><span data-stu-id="aa8df-115">This method extends the [FunctionIDMapper](functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="aa8df-116">Dane klienta są używane do rozróżnienia między środowiskami uruchomieniowymi.</span><span class="sxs-lookup"><span data-stu-id="aa8df-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa8df-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa8df-117">Requirements</span></span>  
 <span data-ttu-id="aa8df-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa8df-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa8df-119">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="aa8df-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="aa8df-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aa8df-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa8df-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa8df-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa8df-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa8df-122">See also</span></span>

- [<span data-ttu-id="aa8df-123">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="aa8df-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="aa8df-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="aa8df-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="aa8df-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="aa8df-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="aa8df-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="aa8df-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="aa8df-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="aa8df-127">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="aa8df-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="aa8df-128">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="aa8df-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="aa8df-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="aa8df-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="aa8df-130">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="aa8df-131">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="aa8df-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
