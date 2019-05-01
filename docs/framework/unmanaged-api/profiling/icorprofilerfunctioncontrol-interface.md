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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 721ee27522b316a561e2f64a322c225cb85a44c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992176"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="12649-102">ICorProfilerFunctionControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="12649-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="12649-103">Udostępnia metody, które umożliwiają programowi profilującemu kodu komunikacji plików wykonywalnych języka wspólnego (CLR) do kontrolowania, jak kompilator JIT ma generować kod ponownej kompilacji określonej metody.</span><span class="sxs-lookup"><span data-stu-id="12649-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12649-104">Metody</span><span class="sxs-lookup"><span data-stu-id="12649-104">Methods</span></span>  
  
|<span data-ttu-id="12649-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="12649-105">Method</span></span>|<span data-ttu-id="12649-106">Opis</span><span class="sxs-lookup"><span data-stu-id="12649-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12649-107">SetCodegenFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="12649-107">SetCodegenFlags Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="12649-108">Ustawia flagi co najmniej jeden z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) wyliczenia do sterowania generowanie kodu dla just-in-time (JIT) ponownie kompilowana funkcji.</span><span class="sxs-lookup"><span data-stu-id="12649-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="12649-109">SetILFunctionBody, metoda</span><span class="sxs-lookup"><span data-stu-id="12649-109">SetILFunctionBody Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="12649-110">Zastępuje treść wspólnego języka pośredniego (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="12649-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="12649-111">SetILInstrumentedCodeMap, metoda</span><span class="sxs-lookup"><span data-stu-id="12649-111">SetILInstrumentedCodeMap Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="12649-112">Ustawia mapę kodu dla określonej funkcji przy użyciu określonego wpisy mapy wspólny język pośredni (CIL).</span><span class="sxs-lookup"><span data-stu-id="12649-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12649-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12649-113">Remarks</span></span>  
 <span data-ttu-id="12649-114">`ICorProfilerFunctionControl` Interfejs zapewnia metody umożliwiają sterowanie generowanie kodu dla jednej funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="12649-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="12649-115">Program profilujący uzyskuje wystąpienie ten interfejs, za pośrednictwem [icorprofilercallback4::getrejitparameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="12649-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="12649-116">Każde wystąpienie `ICorProfilerFunctionControl` kontroluje wszystkie wystąpienia elementu jednej funkcji.</span><span class="sxs-lookup"><span data-stu-id="12649-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12649-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12649-117">Requirements</span></span>  
 <span data-ttu-id="12649-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12649-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12649-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12649-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12649-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12649-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12649-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12649-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12649-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12649-122">See also</span></span>

- [<span data-ttu-id="12649-123">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="12649-123">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="12649-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="12649-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="12649-125">EnumJITedFunctions2, metoda</span><span class="sxs-lookup"><span data-stu-id="12649-125">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
