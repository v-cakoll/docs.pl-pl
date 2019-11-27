---
title: ICorProfilerCallback3::InitializeForAttach — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: 047516574595f9ffcd61360f51823da73a2f9733
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439515"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="06b9c-102">ICorProfilerCallback3::InitializeForAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="06b9c-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="06b9c-103">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby Profiler mógł zainicjować swój stan po operacji dołączania.</span><span class="sxs-lookup"><span data-stu-id="06b9c-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06b9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06b9c-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06b9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06b9c-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="06b9c-106">podczas Wskaźnik interfejsu dla interfejsu `ICorProfilerInfo*`.</span><span class="sxs-lookup"><span data-stu-id="06b9c-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="06b9c-107">podczas Wskaźnik do danych przesłany do metody [IClrProfiling:: AttachProfiler —](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) w parametrze `pvClientData`.</span><span class="sxs-lookup"><span data-stu-id="06b9c-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="06b9c-108">Jeśli ten parametr ma wartość null, `cbClientData` będzie równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="06b9c-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="06b9c-109">Środowisko CLR zwalnia tę pamięć po powrocie z `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="06b9c-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="06b9c-110">podczas Rozmiar, w bajtach, danych, do których wskazuje `pvClientData`.</span><span class="sxs-lookup"><span data-stu-id="06b9c-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06b9c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06b9c-111">Remarks</span></span>  
 <span data-ttu-id="06b9c-112">Wywołania CLR `InitializeForAttach`, aby dać profilerowi możliwość żądania wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="06b9c-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06b9c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06b9c-113">Requirements</span></span>  
 <span data-ttu-id="06b9c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06b9c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06b9c-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="06b9c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06b9c-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06b9c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06b9c-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06b9c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06b9c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06b9c-118">See also</span></span>

- [<span data-ttu-id="06b9c-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="06b9c-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="06b9c-120">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="06b9c-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="06b9c-121">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="06b9c-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="06b9c-122">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="06b9c-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
