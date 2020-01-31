---
title: COR_PRF_CODEGEN_FLAGS — Wyliczanie
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: 4dd4e39c9092d018f13e3bd2822e9492d71141ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867298"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="79fb7-102">COR_PRF_CODEGEN_FLAGS — Wyliczanie</span><span class="sxs-lookup"><span data-stu-id="79fb7-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="79fb7-103">Definiuje flagi generowania kodu, które można ustawić za pomocą metody [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="79fb7-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79fb7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79fb7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="79fb7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="79fb7-105">Members</span></span>  
  
|<span data-ttu-id="79fb7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="79fb7-106">Member</span></span>|<span data-ttu-id="79fb7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="79fb7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="79fb7-108">Żadna funkcja nie zostanie zakreślona w treści tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="79fb7-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="79fb7-109">Jednak sama funkcja może być wbudowana w jej obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="79fb7-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="79fb7-110">Wszystkie optymalizacje zostaną wyłączone dla treści tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="79fb7-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="79fb7-111">Jednak sama funkcja może być w dalszym ciągu zakreślona w jego wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="79fb7-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79fb7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79fb7-112">Remarks</span></span>  
 <span data-ttu-id="79fb7-113">Wyliczenie `COR_PRF_CODEGEN_FLAGS` jest używane przez metodę [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) w celu umożliwienia profilerowi sterowania generowaniem kodu dla funkcji ponownie skompilowanej JIT.</span><span class="sxs-lookup"><span data-stu-id="79fb7-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79fb7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="79fb7-114">Requirements</span></span>  
 <span data-ttu-id="79fb7-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79fb7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79fb7-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="79fb7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79fb7-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="79fb7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79fb7-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79fb7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79fb7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79fb7-119">See also</span></span>

- [<span data-ttu-id="79fb7-120">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="79fb7-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
