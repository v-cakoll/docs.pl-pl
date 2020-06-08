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
ms.openlocfilehash: c2c7ae7a8930949c79b5e24e2da75f3b4649e7f6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500991"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="305f0-102">COR_PRF_CODEGEN_FLAGS — Wyliczanie</span><span class="sxs-lookup"><span data-stu-id="305f0-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="305f0-103">Definiuje flagi generowania kodu, które można ustawić za pomocą metody [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="305f0-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="305f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="305f0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="305f0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="305f0-105">Members</span></span>  
  
|<span data-ttu-id="305f0-106">Członek</span><span class="sxs-lookup"><span data-stu-id="305f0-106">Member</span></span>|<span data-ttu-id="305f0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="305f0-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="305f0-108">Żadna funkcja nie zostanie zakreślona w treści tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="305f0-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="305f0-109">Jednak sama funkcja może być wbudowana w jej obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="305f0-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="305f0-110">Wszystkie optymalizacje zostaną wyłączone dla treści tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="305f0-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="305f0-111">Jednak sama funkcja może być w dalszym ciągu zakreślona w jego wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="305f0-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="305f0-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="305f0-112">Remarks</span></span>  
 <span data-ttu-id="305f0-113">`COR_PRF_CODEGEN_FLAGS`Wyliczenie jest używane przez metodę [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) , aby umożliwić profilerowi sterowanie generowaniem kodu dla funkcji ponownie skompilowanej JIT.</span><span class="sxs-lookup"><span data-stu-id="305f0-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="305f0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="305f0-114">Requirements</span></span>  
 <span data-ttu-id="305f0-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="305f0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="305f0-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="305f0-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="305f0-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="305f0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="305f0-118">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="305f0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="305f0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="305f0-119">See also</span></span>

- [<span data-ttu-id="305f0-120">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="305f0-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
