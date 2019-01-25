---
title: ICorProfilerCallback::ClassUnloadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 217e0942e523b533656f4d194d2b3e3ec63c6db7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683352"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="8b874-102">ICorProfilerCallback::ClassUnloadStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b874-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="8b874-103">Powiadamia program profilujący, że klasa jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="8b874-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b874-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b874-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b874-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b874-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="8b874-106">[in] Określa klasę, która jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="8b874-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b874-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b874-107">Remarks</span></span>  
 <span data-ttu-id="8b874-108">Wartość `classId` jest nieprawidłowa dla żądania informacji po `ClassUnloadStarted` metoda zwraca — to jest profiler ostatniego masz szansę, aby uzyskać informacje na temat tej klasy.</span><span class="sxs-lookup"><span data-stu-id="8b874-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b874-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b874-109">Requirements</span></span>  
 <span data-ttu-id="8b874-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b874-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b874-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b874-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b874-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b874-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b874-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b874-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b874-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b874-114">See also</span></span>
- [<span data-ttu-id="8b874-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b874-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8b874-116">ClassUnloadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="8b874-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
