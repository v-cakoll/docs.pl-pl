---
title: ICorProfilerInfo::SetILFunctionBody — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: da81bd3e255898543c94d4ac64c6afbf39b6bdba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449881"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="5f052-102">ICorProfilerInfo::SetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f052-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="5f052-103">Zastępuje treść określonej funkcji w określonym module.</span><span class="sxs-lookup"><span data-stu-id="5f052-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f052-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f052-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f052-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f052-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="5f052-106">podczas Identyfikator modułu, w którym znajduje się funkcja.</span><span class="sxs-lookup"><span data-stu-id="5f052-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="5f052-107">podczas Token funkcji, dla której ma zostać zamieniony treść.</span><span class="sxs-lookup"><span data-stu-id="5f052-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="5f052-108">podczas Nowy nagłówek dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="5f052-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f052-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f052-109">Remarks</span></span>  
 <span data-ttu-id="5f052-110">Metoda `SetILFunctionBody` zastępuje względny adres wirtualny funkcji w metadanych, tak aby wskazywała nową treść funkcji i dostosowuje wszystkie wewnętrzne struktury danych zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="5f052-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="5f052-111">Metodę `SetILFunctionBody` można wywołać tylko w funkcjach, które nigdy nie zostały skompilowane przez kompilator just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="5f052-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="5f052-112">Użyj metody [ICorProfilerInfo:: GetILFunctionBodyAllocator —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) , aby przydzielić miejsce dla nowej metody w celu zapewnienia, że bufor jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="5f052-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f052-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f052-113">Requirements</span></span>  
 <span data-ttu-id="5f052-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f052-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f052-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5f052-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f052-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5f052-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f052-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f052-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f052-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f052-118">See also</span></span>

- [<span data-ttu-id="5f052-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f052-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
