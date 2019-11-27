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
ms.openlocfilehash: 72531dc4fa7a8afc3bd719d73389fac94e3363bb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439142"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="ff3c9-102">ICorProfilerInfo::GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="ff3c9-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="ff3c9-103">Pobiera identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="ff3c9-103">Gets the ID of a function.</span></span> <span data-ttu-id="ff3c9-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="ff3c9-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="ff3c9-105">Zamiast tego użyj metody [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ff3c9-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff3c9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff3c9-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="ff3c9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff3c9-107">Remarks</span></span>  
 <span data-ttu-id="ff3c9-108">Metoda `GetFunctionFromToken` nie będzie działać dla funkcji ogólnych ani funkcji w typach ogólnych; jest ona już przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ff3c9-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="ff3c9-109">Użyj `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` dla wszystkich funkcji.</span><span class="sxs-lookup"><span data-stu-id="ff3c9-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff3c9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff3c9-110">Requirements</span></span>  
 <span data-ttu-id="ff3c9-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff3c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff3c9-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ff3c9-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff3c9-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ff3c9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff3c9-114">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="ff3c9-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff3c9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff3c9-115">See also</span></span>

- [<span data-ttu-id="ff3c9-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="ff3c9-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
