---
title: COR_PRF_TRANSITION_REASON — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: e890c62a54654e86bb4a825613807efe142c8d5a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500744"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="ffa8a-102">COR_PRF_TRANSITION_REASON — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ffa8a-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="ffa8a-103">Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="ffa8a-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffa8a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="ffa8a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ffa8a-105">Members</span></span>  
  
|<span data-ttu-id="ffa8a-106">Członek</span><span class="sxs-lookup"><span data-stu-id="ffa8a-106">Member</span></span>|<span data-ttu-id="ffa8a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ffa8a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="ffa8a-108">Przejście jest spowodowane wywołaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="ffa8a-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="ffa8a-109">Przejście jest spowodowane zwracaniem z funkcji.</span><span class="sxs-lookup"><span data-stu-id="ffa8a-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffa8a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffa8a-110">Remarks</span></span>  
 <span data-ttu-id="ffa8a-111">Gdy następuje przejście, profiler otrzymuje wywołanie [ICorProfilerCallback:: ManagedToUnmanagedTransition —](icorprofilercallback-managedtounmanagedtransition-method.md) lub [ICorProfilerCallback:: UnmanagedToManagedTransition —](icorprofilercallback-unmanagedtomanagedtransition-method.md) , z którego każda zawiera wartość `COR_PRF_TRANSITION_REASON` wyliczenia, aby wskazać przyczynę przejścia.</span><span class="sxs-lookup"><span data-stu-id="ffa8a-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffa8a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffa8a-112">Requirements</span></span>  
 <span data-ttu-id="ffa8a-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffa8a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffa8a-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ffa8a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ffa8a-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ffa8a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffa8a-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffa8a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
