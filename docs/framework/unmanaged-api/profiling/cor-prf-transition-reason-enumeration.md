---
title: "COR_PRF_TRANSITION_REASON — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_TRANSITION_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_TRANSITION_REASON
helpviewer_keywords: COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f11b5fb5409ee30b0456e0c562545718ed46bb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="5d93f-102">COR_PRF_TRANSITION_REASON — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5d93f-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="5d93f-103">Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="5d93f-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d93f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d93f-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="5d93f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5d93f-105">Members</span></span>  
  
|<span data-ttu-id="5d93f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5d93f-106">Member</span></span>|<span data-ttu-id="5d93f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5d93f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="5d93f-108">Przejście jest spowodowane wywołaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="5d93f-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="5d93f-109">Przejście jest ze względu na typ zwracany funkcji.</span><span class="sxs-lookup"><span data-stu-id="5d93f-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d93f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d93f-110">Remarks</span></span>  
 <span data-ttu-id="5d93f-111">W przypadku przejścia profilera odbiera [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) lub [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) wywołania zwrotnego, albo z nich udostępnia wartość `COR_PRF_TRANSITION_REASON` wyliczeniu, aby wskazać przyczynę przejścia.</span><span class="sxs-lookup"><span data-stu-id="5d93f-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d93f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d93f-112">Requirements</span></span>  
 <span data-ttu-id="5d93f-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d93f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d93f-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d93f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d93f-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d93f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d93f-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d93f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
