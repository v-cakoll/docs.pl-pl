---
title: COR_PRF_EX_CLAUSE_INFO — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3cf8b8735fc10b741d13b041eedc3e96607bef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="a04d6-102">COR_PRF_EX_CLAUSE_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="a04d6-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="a04d6-103">Przechowuje informacje dotyczące wystąpienia klauzuli określonego wyjątku i jego skojarzony ramki.</span><span class="sxs-lookup"><span data-stu-id="a04d6-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a04d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a04d6-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="a04d6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a04d6-105">Members</span></span>  
  
|<span data-ttu-id="a04d6-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a04d6-106">Member</span></span>|<span data-ttu-id="a04d6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a04d6-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="a04d6-108">Wartość [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) wyliczenie określający typ wyjątku klauzuli właśnie wprowadzony kod lub w lewo.</span><span class="sxs-lookup"><span data-stu-id="a04d6-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="a04d6-109">Punkt wejścia natywnej obsługi klauzuli — na przykład zawartość rejestru X86 EIP.</span><span class="sxs-lookup"><span data-stu-id="a04d6-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="a04d6-110">Wskaźnik do logicznego ramki obsługi klauzuli — na przykład zawartość rejestru X86 EBP.</span><span class="sxs-lookup"><span data-stu-id="a04d6-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="a04d6-111">Wskaźnik stosu cienia.</span><span class="sxs-lookup"><span data-stu-id="a04d6-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="a04d6-112">Ta wartość jest zawartość rejestru podstawowego dostawcy i dotyczy tylko IA64.</span><span class="sxs-lookup"><span data-stu-id="a04d6-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a04d6-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a04d6-113">Remarks</span></span>  
 <span data-ttu-id="a04d6-114">Po otrzymaniu powiadomienia wyjątek [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) może służyć do Pobierz natywnego adresu i ramki informacje dla klauzuli wyjątek (`catch` / `finally`/filtrować) ma być uruchomiona albo został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a04d6-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="a04d6-115">Wykonywanie klauzuli wyjątek polega na te wywołania zwrotne z środowisko uruchomieniowe języka wspólnego (CLR):</span><span class="sxs-lookup"><span data-stu-id="a04d6-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
-   [<span data-ttu-id="a04d6-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="a04d6-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [<span data-ttu-id="a04d6-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="a04d6-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [<span data-ttu-id="a04d6-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="a04d6-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [<span data-ttu-id="a04d6-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="a04d6-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [<span data-ttu-id="a04d6-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="a04d6-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [<span data-ttu-id="a04d6-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="a04d6-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="a04d6-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a04d6-122">Requirements</span></span>  
 <span data-ttu-id="a04d6-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a04d6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a04d6-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a04d6-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a04d6-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a04d6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a04d6-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a04d6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a04d6-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a04d6-127">See Also</span></span>  
 [<span data-ttu-id="a04d6-128">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="a04d6-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
