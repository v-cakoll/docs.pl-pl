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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab5612a2bb48b2cc93e0150f45107e474a4e6217
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452120"
---
# <a name="corprfcodegenflags-enumeration"></a><span data-ttu-id="fe636-102">COR_PRF_CODEGEN_FLAGS — Wyliczanie</span><span class="sxs-lookup"><span data-stu-id="fe636-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="fe636-103">Określa flagi generowania kodu, które można ustawić za pomocą [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fe636-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe636-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe636-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="fe636-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fe636-105">Members</span></span>  
  
|<span data-ttu-id="fe636-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fe636-106">Member</span></span>|<span data-ttu-id="fe636-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fe636-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="fe636-108">Nie funkcje będą wbudowana w treści tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="fe636-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="fe636-109">Jednak ta funkcja może być wbudowana w jego obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="fe636-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="fe636-110">Wszystkie optymalizacje zostanie wyłączony dla tej funkcji treści.</span><span class="sxs-lookup"><span data-stu-id="fe636-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="fe636-111">Jednak ta funkcja może nadal być wbudowana w jego obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="fe636-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe636-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe636-112">Remarks</span></span>  
 <span data-ttu-id="fe636-113">`COR_PRF_CODEGEN_FLAGS` Wyliczenie jest używany przez [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metodę umożliwiającą włączenie profiler do kontrolowania generowanie kodu dla funkcji ponownie kompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="fe636-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe636-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe636-114">Requirements</span></span>  
 <span data-ttu-id="fe636-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe636-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe636-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe636-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe636-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe636-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe636-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe636-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe636-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe636-119">See Also</span></span>  
 [<span data-ttu-id="fe636-120">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fe636-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
