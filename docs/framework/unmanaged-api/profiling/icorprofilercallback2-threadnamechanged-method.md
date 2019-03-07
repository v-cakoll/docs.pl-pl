---
title: ICorProfilerCallback2::ThreadNameChanged — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0102c2b8269d8a716a75b3f411b8e177f500eb4a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470578"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="27ff9-102">ICorProfilerCallback2::ThreadNameChanged — Metoda</span><span class="sxs-lookup"><span data-stu-id="27ff9-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="27ff9-103">Powiadamia program profilujący kodu, że zmieniono nazwę wątku.</span><span class="sxs-lookup"><span data-stu-id="27ff9-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27ff9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27ff9-104">Syntax</span></span>  
  
```  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27ff9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27ff9-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="27ff9-106">[in] Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="27ff9-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="27ff9-107">[in] Długość nazwy nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="27ff9-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="27ff9-108">[in] Nowa nazwa wątku.</span><span class="sxs-lookup"><span data-stu-id="27ff9-108">[in] The new name of the thread.</span></span> <span data-ttu-id="27ff9-109">Nazwa jest nie zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="27ff9-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27ff9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27ff9-110">Requirements</span></span>  
 <span data-ttu-id="27ff9-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27ff9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27ff9-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27ff9-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27ff9-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27ff9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27ff9-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27ff9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ff9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27ff9-115">See also</span></span>
- [<span data-ttu-id="27ff9-116">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="27ff9-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="27ff9-117">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="27ff9-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
