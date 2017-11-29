---
title: "ICorProfilerCallback3::InitializeForAttach — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3.InitializeForAttach Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 323f163774407ff2ddfd261ff6d6584a07ed7d8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="9417a-102">ICorProfilerCallback3::InitializeForAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="9417a-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="9417a-103">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby zapewnić możliwość zainicjować stanu po operacji dołączania profilera.</span><span class="sxs-lookup"><span data-stu-id="9417a-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9417a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9417a-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9417a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9417a-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="9417a-106">[in] Wskaźnik interfejsu dla `ICorProfilerInfo*` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9417a-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="9417a-107">[in] Wskaźnik do danych przekazany do [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metody w jego `pvClientData` parametru.</span><span class="sxs-lookup"><span data-stu-id="9417a-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="9417a-108">Jeśli ten parametr ma wartość null, `cbClientData` będzie równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="9417a-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="9417a-109">Środowisko CLR zwalnia pamięć taka zwrócona z `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="9417a-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="9417a-110">[in] Rozmiar w bajtach danych który `pvClientData` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="9417a-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9417a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9417a-111">Remarks</span></span>  
 <span data-ttu-id="9417a-112">Wywołania CLR `InitializeForAttach` zapewnienie profilera możliwość wywołania zwrotne żądania.</span><span class="sxs-lookup"><span data-stu-id="9417a-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9417a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9417a-113">Requirements</span></span>  
 <span data-ttu-id="9417a-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9417a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9417a-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9417a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9417a-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9417a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9417a-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9417a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9417a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9417a-118">See Also</span></span>  
 [<span data-ttu-id="9417a-119">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="9417a-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9417a-120">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="9417a-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="9417a-121">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="9417a-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="9417a-122">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="9417a-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
