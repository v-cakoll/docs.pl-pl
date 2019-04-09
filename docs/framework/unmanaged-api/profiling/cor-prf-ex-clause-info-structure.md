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
ms.openlocfilehash: 5e12410ab9886055dca8c3f9103c1e56475c2d5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140351"
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="58efb-102">COR_PRF_EX_CLAUSE_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="58efb-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="58efb-103">Przechowuje informacje dotyczące wystąpienia klauzuli określony wyjątek i jego skojarzone ramki.</span><span class="sxs-lookup"><span data-stu-id="58efb-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58efb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58efb-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="58efb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="58efb-105">Members</span></span>  
  
|<span data-ttu-id="58efb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="58efb-106">Member</span></span>|<span data-ttu-id="58efb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="58efb-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="58efb-108">Wartość [cor_prf_clause_type —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) wyliczenie, które określa typ wyjątku klauzulę po prostu wprowadzony kod lub po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="58efb-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="58efb-109">Punkt wejścia natywnej obsługi klauzuli — na przykład zawartość rejestru X86 EIP.</span><span class="sxs-lookup"><span data-stu-id="58efb-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="58efb-110">Wskaźnik do ramki logiczne klauzuli obsługi — na przykład zawartość rejestru X86 EBP.</span><span class="sxs-lookup"><span data-stu-id="58efb-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="58efb-111">Wskaźnik stosu w tle.</span><span class="sxs-lookup"><span data-stu-id="58efb-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="58efb-112">Ta wartość jest zawartość rejestru BSP i ma zastosowanie tylko do IA64.</span><span class="sxs-lookup"><span data-stu-id="58efb-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58efb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58efb-113">Remarks</span></span>  
 <span data-ttu-id="58efb-114">Po odebraniu powiadomienia wyjątku [icorprofilerinfo2::getnotifiedexceptionclauseinfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) pozwala uzyskać natywnych informacje dotyczące adresów i ramki dla klauzuli wyjątek (`catch` / `finally`/filtrować) który ma być uruchomiona lub została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="58efb-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="58efb-115">Wykonywanie klauzuli wyjątek polega na te wywołania zwrotne z środowisko uruchomieniowe języka wspólnego (CLR):</span><span class="sxs-lookup"><span data-stu-id="58efb-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
-   [<span data-ttu-id="58efb-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="58efb-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [<span data-ttu-id="58efb-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="58efb-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [<span data-ttu-id="58efb-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="58efb-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [<span data-ttu-id="58efb-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="58efb-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [<span data-ttu-id="58efb-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="58efb-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [<span data-ttu-id="58efb-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="58efb-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="58efb-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58efb-122">Requirements</span></span>  
 <span data-ttu-id="58efb-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58efb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58efb-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="58efb-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="58efb-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58efb-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="58efb-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="58efb-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="58efb-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58efb-127">See also</span></span>

- [<span data-ttu-id="58efb-128">Profiling — Struktury</span><span class="sxs-lookup"><span data-stu-id="58efb-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
