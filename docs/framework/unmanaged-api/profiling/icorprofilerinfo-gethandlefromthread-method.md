---
title: ICorProfilerInfo::GetHandleFromThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 419195d9450bf07e5ad8c7cedcac76e175137c96
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498222"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="2b8f7-102">ICorProfilerInfo::GetHandleFromThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="2b8f7-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="2b8f7-103">Mapuje identyfikator wątku na dojście wątku Win32.</span><span class="sxs-lookup"><span data-stu-id="2b8f7-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b8f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b8f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b8f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b8f7-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="2b8f7-106">podczas Identyfikator wątku, który ma zostać zamapowany.</span><span class="sxs-lookup"><span data-stu-id="2b8f7-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="2b8f7-107">określoną Wskaźnik do dojścia do wątku Win32.</span><span class="sxs-lookup"><span data-stu-id="2b8f7-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b8f7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b8f7-108">Remarks</span></span>  
 <span data-ttu-id="2b8f7-109">Profiler musi wywołać `DuplicateHandle` funkcję Win32 w uchwycie przed użyciem go.</span><span class="sxs-lookup"><span data-stu-id="2b8f7-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b8f7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b8f7-110">Requirements</span></span>  
 <span data-ttu-id="2b8f7-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b8f7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b8f7-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2b8f7-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b8f7-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2b8f7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b8f7-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b8f7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8f7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b8f7-115">See also</span></span>

- [<span data-ttu-id="2b8f7-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b8f7-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
