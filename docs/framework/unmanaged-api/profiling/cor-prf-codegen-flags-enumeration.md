---
title: "COR_PRF_CODEGEN_FLAGS — Wyliczanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CODEGEN_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CODEGEN_FLAGS
helpviewer_keywords: COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fc50330b31e8b0f8def24aaafbf3a4b7e365e98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfcodegenflags-enumeration"></a><span data-ttu-id="e6bae-102">COR_PRF_CODEGEN_FLAGS — Wyliczanie</span><span class="sxs-lookup"><span data-stu-id="e6bae-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="e6bae-103">Określa flagi generowania kodu, które można ustawić za pomocą [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e6bae-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6bae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6bae-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e6bae-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e6bae-105">Members</span></span>  
  
|<span data-ttu-id="e6bae-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e6bae-106">Member</span></span>|<span data-ttu-id="e6bae-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e6bae-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="e6bae-108">Nie funkcje będą wbudowana w treści tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e6bae-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="e6bae-109">Jednak ta funkcja może być wbudowana w jego obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="e6bae-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="e6bae-110">Wszystkie optymalizacje zostanie wyłączony dla tej funkcji treści.</span><span class="sxs-lookup"><span data-stu-id="e6bae-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="e6bae-111">Jednak ta funkcja może nadal być wbudowana w jego obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="e6bae-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6bae-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6bae-112">Remarks</span></span>  
 <span data-ttu-id="e6bae-113">`COR_PRF_CODEGEN_FLAGS` Wyliczenie jest używany przez [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metodę umożliwiającą włączenie profiler do kontrolowania generowanie kodu dla funkcji ponownie kompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="e6bae-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6bae-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6bae-114">Requirements</span></span>  
 <span data-ttu-id="e6bae-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6bae-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6bae-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e6bae-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6bae-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6bae-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6bae-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6bae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6bae-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6bae-119">See Also</span></span>  
 [<span data-ttu-id="e6bae-120">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e6bae-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
