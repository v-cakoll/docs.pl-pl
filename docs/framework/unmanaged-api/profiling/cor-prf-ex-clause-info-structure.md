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
ms.openlocfilehash: fb6d2e5fc21047fea0928137f983c553f9bb2bbd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867285"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="5d950-102">COR_PRF_EX_CLAUSE_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="5d950-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="5d950-103">Przechowuje informacje o konkretnym wystąpieniu klauzuli wyjątku i skojarzonej z nią ramce.</span><span class="sxs-lookup"><span data-stu-id="5d950-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d950-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d950-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="5d950-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5d950-105">Members</span></span>  
  
|<span data-ttu-id="5d950-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5d950-106">Member</span></span>|<span data-ttu-id="5d950-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5d950-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="5d950-108">Wartość wyliczenia [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) , która określa typ klauzuli wyjątku, która właśnie została wprowadzona lub po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="5d950-108">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="5d950-109">Natywny punkt wejścia procedury obsługi klauzuli — na przykład zawartość rejestru EIP klasy x86.</span><span class="sxs-lookup"><span data-stu-id="5d950-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="5d950-110">Wskaźnik do ramki logicznej programu obsługi klauzuli — na przykład zawartość rejestru x86 EBP.</span><span class="sxs-lookup"><span data-stu-id="5d950-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="5d950-111">Wskaźnik do stosu cienia.</span><span class="sxs-lookup"><span data-stu-id="5d950-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="5d950-112">Ta wartość jest zawartością rejestru zestawu Winsock i ma zastosowanie tylko do IA64.</span><span class="sxs-lookup"><span data-stu-id="5d950-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d950-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d950-113">Remarks</span></span>  
 <span data-ttu-id="5d950-114">Po otrzymaniu powiadomienia o wyjątku [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo —](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) może służyć do uzyskiwania informacji o adresie i ramce natywnej dla klauzuli wyjątku (`catch`/`finally`/Filter), która ma zostać uruchomiona lub właśnie została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="5d950-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="5d950-115">Wykonanie klauzuli wyjątku obejmuje te wywołania zwrotne z aparatu plików wykonywalnych języka wspólnego (CLR):</span><span class="sxs-lookup"><span data-stu-id="5d950-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="5d950-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="5d950-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="5d950-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="5d950-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="5d950-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="5d950-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="5d950-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="5d950-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="5d950-120">ICorProfilerCallback:: ExceptionUnwindFinallyLeave —</span><span class="sxs-lookup"><span data-stu-id="5d950-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="5d950-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="5d950-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="5d950-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d950-122">Requirements</span></span>  
 <span data-ttu-id="5d950-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d950-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d950-124">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="5d950-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5d950-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5d950-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d950-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d950-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d950-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d950-127">See also</span></span>

- [<span data-ttu-id="5d950-128">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="5d950-128">Profiling Structures</span></span>](profiling-structures.md)
