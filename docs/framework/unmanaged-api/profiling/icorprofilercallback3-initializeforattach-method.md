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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ebdd76655124922008667898e38f873ad93598e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555599"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="ec810-102">ICorProfilerCallback3::InitializeForAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec810-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="ec810-103">Metoda wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR), aby dać profilerowi możliwość zainicjowania jego stanu po operacji dołączania.</span><span class="sxs-lookup"><span data-stu-id="ec810-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec810-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec810-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec810-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec810-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="ec810-106">[in] Wskaźnik interfejsu do `ICorProfilerInfo*` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ec810-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="ec810-107">[in] Wskaźnik do danych jest przekazywany do [iclrprofiling::attachprofiler —](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in Class metoda jego `pvClientData` parametru.</span><span class="sxs-lookup"><span data-stu-id="ec810-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="ec810-108">Jeśli ten parametr ma wartość null, `cbClientData` będzie mieć wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="ec810-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="ec810-109">Środowisko CLR zwalnia ta pamięć zwrócona z `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="ec810-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="ec810-110">[in] Rozmiar w bajtach, danych, który `pvClientData` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="ec810-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec810-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec810-111">Remarks</span></span>  
 <span data-ttu-id="ec810-112">CLR wywołuje `InitializeForAttach` aby dać profilerowi możliwość na wywołania zwrotne żądania.</span><span class="sxs-lookup"><span data-stu-id="ec810-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec810-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec810-113">Requirements</span></span>  
 <span data-ttu-id="ec810-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec810-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec810-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec810-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec810-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec810-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec810-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec810-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec810-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec810-118">See also</span></span>
- [<span data-ttu-id="ec810-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec810-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ec810-120">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec810-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ec810-121">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="ec810-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ec810-122">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="ec810-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
