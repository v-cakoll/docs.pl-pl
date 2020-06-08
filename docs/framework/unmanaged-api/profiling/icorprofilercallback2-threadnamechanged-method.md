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
ms.openlocfilehash: 3eb108ed20d0fd1287cb82eb4d552206aeae15d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499730"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="9aa63-102">ICorProfilerCallback2::ThreadNameChanged — Metoda</span><span class="sxs-lookup"><span data-stu-id="9aa63-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="9aa63-103">Powiadamia profiler kodu o zmianie nazwy wątku.</span><span class="sxs-lookup"><span data-stu-id="9aa63-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa63-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9aa63-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9aa63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9aa63-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="9aa63-106">podczas Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="9aa63-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9aa63-107">podczas Długość nowej nazwy wątku.</span><span class="sxs-lookup"><span data-stu-id="9aa63-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="9aa63-108">podczas Nowa nazwa wątku.</span><span class="sxs-lookup"><span data-stu-id="9aa63-108">[in] The new name of the thread.</span></span> <span data-ttu-id="9aa63-109">Nazwa nie jest zakończona wartością null.</span><span class="sxs-lookup"><span data-stu-id="9aa63-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aa63-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9aa63-110">Requirements</span></span>  
 <span data-ttu-id="9aa63-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aa63-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aa63-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9aa63-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9aa63-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9aa63-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9aa63-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aa63-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa63-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9aa63-115">See also</span></span>

- [<span data-ttu-id="9aa63-116">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9aa63-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9aa63-117">ICorProfilerCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9aa63-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
