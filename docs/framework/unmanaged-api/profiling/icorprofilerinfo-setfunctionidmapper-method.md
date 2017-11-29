---
title: "ICorProfilerInfo::SetFunctionIDMapper — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetFunctionIDMapper
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7caaecdbd73a183e2d188a2ab9e799c5eb3efaca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="65a91-102">ICorProfilerInfo::SetFunctionIDMapper — Metoda</span><span class="sxs-lookup"><span data-stu-id="65a91-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="65a91-103">Określa zaimplementowana profilera funkcję, która będzie wywoływana w celu mapowania `FunctionID` wartości alternatywne wartości, które są przekazywane do profilera działać punkty zaczepienia wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="65a91-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65a91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65a91-104">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65a91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65a91-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="65a91-106">[in] Wskaźnik do [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementację, która będzie wywoływana w celu mapowania `FunctionID` wartości alternatywne wartości.</span><span class="sxs-lookup"><span data-stu-id="65a91-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65a91-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65a91-107">Remarks</span></span>  
 <span data-ttu-id="65a91-108">Alternatywy dla `FunctionID` wartości zostaną przekazane do punkty zaczepienia wejścia/wyjścia funkcji profilera ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) określono przez [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="65a91-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="65a91-109">`FunctionIDMapper` Można ustawić tylko raz i zalecane jest ustawienie [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="65a91-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65a91-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65a91-110">Requirements</span></span>  
 <span data-ttu-id="65a91-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65a91-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65a91-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65a91-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65a91-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65a91-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65a91-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65a91-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a91-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65a91-115">See Also</span></span>  
 [<span data-ttu-id="65a91-116">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="65a91-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
