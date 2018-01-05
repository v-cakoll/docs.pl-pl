---
title: "ICorProfilerInfo::SetILFunctionBody — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c44fa89ba66a306792f1ffed162447a6305a0347
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="2735a-102">ICorProfilerInfo::SetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="2735a-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="2735a-103">Zastępuje treści określonej funkcji w określonym module.</span><span class="sxs-lookup"><span data-stu-id="2735a-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2735a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2735a-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2735a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2735a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="2735a-106">[in] Identyfikator modułu, w której znajduje się funkcja.</span><span class="sxs-lookup"><span data-stu-id="2735a-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="2735a-107">[in] Token funkcji, dla którego ma zostać zamieniony treści.</span><span class="sxs-lookup"><span data-stu-id="2735a-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="2735a-108">[in] Nagłówek nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="2735a-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2735a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2735a-109">Remarks</span></span>  
 <span data-ttu-id="2735a-110">`SetILFunctionBody` Metoda zastępuje adres względny wirtualnej funkcji w metadanych, który wskazuje nowych treści funkcji i dostosowuje wszelkich struktur danych wewnętrznych, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="2735a-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="2735a-111">`SetILFunctionBody` Metodę można wywołać tylko funkcje, które nigdy nie zostały skompilowane za pomocą kompilatora just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="2735a-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="2735a-112">Użyj [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) metody, aby przydzielić miejsce dla nowej metody upewnić się, że bufor jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="2735a-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2735a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2735a-113">Requirements</span></span>  
 <span data-ttu-id="2735a-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2735a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2735a-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2735a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2735a-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2735a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2735a-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2735a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2735a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2735a-118">See Also</span></span>  
 [<span data-ttu-id="2735a-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="2735a-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
