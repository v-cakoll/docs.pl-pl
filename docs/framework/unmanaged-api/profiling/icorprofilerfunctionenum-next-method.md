---
title: ICorProfilerFunctionEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
ms.openlocfilehash: 2ad4494cf3a429020099b4bd9d961341437fcd1e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447787"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="dff63-102">ICorProfilerFunctionEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="dff63-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="dff63-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span><span class="sxs-lookup"><span data-stu-id="dff63-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff63-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dff63-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dff63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dff63-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="dff63-106">[in] The number of functions to retrieve.</span><span class="sxs-lookup"><span data-stu-id="dff63-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="dff63-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span><span class="sxs-lookup"><span data-stu-id="dff63-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="dff63-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span><span class="sxs-lookup"><span data-stu-id="dff63-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dff63-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dff63-109">Return Value</span></span>  
 <span data-ttu-id="dff63-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span><span class="sxs-lookup"><span data-stu-id="dff63-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dff63-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dff63-111">HRESULT</span></span>|<span data-ttu-id="dff63-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dff63-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dff63-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="dff63-113">S_OK</span></span>|<span data-ttu-id="dff63-114">`celt` elements were returned.</span><span class="sxs-lookup"><span data-stu-id="dff63-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="dff63-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dff63-115">S_FALSE</span></span>|<span data-ttu-id="dff63-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span><span class="sxs-lookup"><span data-stu-id="dff63-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dff63-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dff63-117">Requirements</span></span>  
 <span data-ttu-id="dff63-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dff63-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dff63-119">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dff63-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dff63-120">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dff63-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dff63-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dff63-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff63-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dff63-122">See also</span></span>

- [<span data-ttu-id="dff63-123">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="dff63-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="dff63-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="dff63-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
