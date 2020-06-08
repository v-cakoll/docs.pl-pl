---
title: ICorProfilerFunctionControl — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
ms.openlocfilehash: 177127c8c53e4fee31f7007d04c49cc337cca458
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498729"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="908a5-102">ICorProfilerFunctionControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="908a5-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="908a5-103">Dostarcza metody, które umożliwiają profilerowi kodu komunikowanie się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania, jak kompilator JIT powinien generować kod podczas ponownego kompilowania określonej metody.</span><span class="sxs-lookup"><span data-stu-id="908a5-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="908a5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="908a5-104">Methods</span></span>  
  
|<span data-ttu-id="908a5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="908a5-105">Method</span></span>|<span data-ttu-id="908a5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="908a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="908a5-107">SetCodegenFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="908a5-107">SetCodegenFlags Method</span></span>](icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="908a5-108">Ustawia co najmniej jedną flagę z wyliczenia [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) , aby kontrolować generowanie kodu dla funkcji rekompilowanej just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="908a5-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="908a5-109">SetILFunctionBody, metoda</span><span class="sxs-lookup"><span data-stu-id="908a5-109">SetILFunctionBody Method</span></span>](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="908a5-110">Zastępuje treść wspólnego języka pośredniego (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="908a5-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="908a5-111">SetILInstrumentedCodeMap, metoda</span><span class="sxs-lookup"><span data-stu-id="908a5-111">SetILInstrumentedCodeMap Method</span></span>](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="908a5-112">Ustawia mapę kodu dla określonej funkcji przy użyciu określonych wpisów mapy typowego języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="908a5-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="908a5-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="908a5-113">Remarks</span></span>  
 <span data-ttu-id="908a5-114">`ICorProfilerFunctionControl`Interfejs zapewnia metody kontrolujące generowanie kodu dla pojedynczej ponownie skompilowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="908a5-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="908a5-115">Profiler uzyskuje wystąpienie tego interfejsu za pomocą wywołania zwrotnego [ICorProfilerCallback4:: GetReJITParameters —](icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="908a5-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="908a5-116">Każde wystąpienie `ICorProfilerFunctionControl` formantów kontroluje wszystkie wystąpienia jednej funkcji.</span><span class="sxs-lookup"><span data-stu-id="908a5-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="908a5-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="908a5-117">Requirements</span></span>  
 <span data-ttu-id="908a5-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="908a5-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="908a5-119">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="908a5-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="908a5-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="908a5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="908a5-121">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="908a5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="908a5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="908a5-122">See also</span></span>

- [<span data-ttu-id="908a5-123">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="908a5-123">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="908a5-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="908a5-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="908a5-125">EnumJITedFunctions2, metoda</span><span class="sxs-lookup"><span data-stu-id="908a5-125">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)
