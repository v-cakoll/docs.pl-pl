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
ms.openlocfilehash: 5c764031f709eefe61022d0662f37bc5d3f3e281
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501004"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="41730-102">COR_PRF_EX_CLAUSE_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="41730-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="41730-103">Przechowuje informacje o konkretnym wystąpieniu klauzuli wyjątku i skojarzonej z nią ramce.</span><span class="sxs-lookup"><span data-stu-id="41730-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41730-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41730-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="41730-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="41730-105">Members</span></span>  
  
|<span data-ttu-id="41730-106">Członek</span><span class="sxs-lookup"><span data-stu-id="41730-106">Member</span></span>|<span data-ttu-id="41730-107">Opis</span><span class="sxs-lookup"><span data-stu-id="41730-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="41730-108">Wartość wyliczenia [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) , która określa typ klauzuli wyjątku, która właśnie została wprowadzona lub po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="41730-108">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="41730-109">Natywny punkt wejścia procedury obsługi klauzuli — na przykład zawartość rejestru EIP klasy x86.</span><span class="sxs-lookup"><span data-stu-id="41730-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="41730-110">Wskaźnik do ramki logicznej programu obsługi klauzuli — na przykład zawartość rejestru x86 EBP.</span><span class="sxs-lookup"><span data-stu-id="41730-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="41730-111">Wskaźnik do stosu cienia.</span><span class="sxs-lookup"><span data-stu-id="41730-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="41730-112">Ta wartość jest zawartością rejestru zestawu Winsock i ma zastosowanie tylko do IA64.</span><span class="sxs-lookup"><span data-stu-id="41730-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41730-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41730-113">Remarks</span></span>  
 <span data-ttu-id="41730-114">Po otrzymaniu powiadomienia o wyjątku [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo —](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) może służyć do uzyskania natywnego adresu i ramki dla klauzuli wyjątku ( `catch` / `finally` /Filter), która ma zostać uruchomiona lub właśnie została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="41730-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="41730-115">Wykonanie klauzuli wyjątku obejmuje te wywołania zwrotne z aparatu plików wykonywalnych języka wspólnego (CLR):</span><span class="sxs-lookup"><span data-stu-id="41730-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="41730-116">ICorProfilerCallback:: ExceptionCatcherEnter —</span><span class="sxs-lookup"><span data-stu-id="41730-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="41730-117">ICorProfilerCallback:: ExceptionUnwindFinallyEnter —</span><span class="sxs-lookup"><span data-stu-id="41730-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="41730-118">ICorProfilerCallback:: ExceptionSearchFilterEnter —</span><span class="sxs-lookup"><span data-stu-id="41730-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="41730-119">ICorProfilerCallback:: ExceptionCatcherLeave —</span><span class="sxs-lookup"><span data-stu-id="41730-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="41730-120">ICorProfilerCallback:: ExceptionUnwindFinallyLeave —</span><span class="sxs-lookup"><span data-stu-id="41730-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="41730-121">ICorProfilerCallback:: ExceptionSearchFilterLeave —</span><span class="sxs-lookup"><span data-stu-id="41730-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="41730-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41730-122">Requirements</span></span>  
 <span data-ttu-id="41730-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41730-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41730-124">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="41730-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="41730-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41730-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41730-126">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41730-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41730-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41730-127">See also</span></span>

- [<span data-ttu-id="41730-128">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="41730-128">Profiling Structures</span></span>](profiling-structures.md)
