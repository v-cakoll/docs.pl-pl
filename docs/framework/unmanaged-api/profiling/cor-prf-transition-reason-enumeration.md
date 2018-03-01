---
title: "COR_PRF_TRANSITION_REASON — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 498abc57e35946b2b0c8bf08cdd768bd7039c9f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="82759-102">COR_PRF_TRANSITION_REASON — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="82759-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="82759-103">Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="82759-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82759-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82759-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="82759-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="82759-105">Members</span></span>  
  
|<span data-ttu-id="82759-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="82759-106">Member</span></span>|<span data-ttu-id="82759-107">Opis</span><span class="sxs-lookup"><span data-stu-id="82759-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="82759-108">Przejście jest spowodowane wywołaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="82759-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="82759-109">Przejście jest ze względu na typ zwracany funkcji.</span><span class="sxs-lookup"><span data-stu-id="82759-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82759-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82759-110">Remarks</span></span>  
 <span data-ttu-id="82759-111">W przypadku przejścia profilera odbiera [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) lub [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) wywołania zwrotnego, albo z nich udostępnia wartość `COR_PRF_TRANSITION_REASON` wyliczeniu, aby wskazać przyczynę przejścia.</span><span class="sxs-lookup"><span data-stu-id="82759-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82759-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82759-112">Requirements</span></span>  
 <span data-ttu-id="82759-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82759-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82759-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="82759-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82759-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82759-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82759-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82759-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
