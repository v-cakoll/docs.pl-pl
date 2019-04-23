---
title: ICorProfilerInfo::GetFunctionFromToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f4fb2292154a2660a2db3f0b3962fcf2114e385
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099979"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="9a0e0-102">ICorProfilerInfo::GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a0e0-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="9a0e0-103">Pobiera identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="9a0e0-103">Gets the ID of a function.</span></span> <span data-ttu-id="9a0e0-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="9a0e0-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="9a0e0-105">Użyj [icorprofilerinfo2::getfunctionfromtokenandtypeargs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="9a0e0-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a0e0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a0e0-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="9a0e0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a0e0-107">Remarks</span></span>  
 <span data-ttu-id="9a0e0-108">`GetFunctionFromToken` Metoda nie będzie działać dla lub funkcji ogólnych w typach ogólnych; jest obecnie przestarzała.</span><span class="sxs-lookup"><span data-stu-id="9a0e0-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="9a0e0-109">Użyj `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` dla wszystkich funkcji.</span><span class="sxs-lookup"><span data-stu-id="9a0e0-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a0e0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a0e0-110">Requirements</span></span>  
 <span data-ttu-id="9a0e0-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a0e0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a0e0-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a0e0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a0e0-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a0e0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a0e0-114">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="9a0e0-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a0e0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a0e0-115">See also</span></span>

- [<span data-ttu-id="9a0e0-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a0e0-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
