---
title: ICorProfilerInfo::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: 45ae164e79f077549a1d685aa060484240546a10
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497962"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="a6b34-102">ICorProfilerInfo::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6b34-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="a6b34-103">Pobiera tożsamość kontekstu aktualnie skojarzoną z określonym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="a6b34-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b34-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6b34-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6b34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6b34-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="a6b34-106">podczas Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="a6b34-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="a6b34-107">określoną Wskaźnik do identyfikatora kontekstu aktualnie skojarzonego z określonym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="a6b34-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="a6b34-108">Jeśli wątek nie ma obecnie skojarzonego kontekstu, ta funkcja zwróci CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="a6b34-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6b34-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6b34-109">Requirements</span></span>  
 <span data-ttu-id="a6b34-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6b34-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6b34-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a6b34-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6b34-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a6b34-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6b34-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6b34-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b34-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6b34-114">See also</span></span>

- [<span data-ttu-id="a6b34-115">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6b34-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
