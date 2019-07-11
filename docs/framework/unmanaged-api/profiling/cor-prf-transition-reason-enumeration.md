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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c22e3c7c04a2b85723f1c0dba4543465faccab58
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745498"
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="0cb13-102">COR_PRF_TRANSITION_REASON — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0cb13-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="0cb13-103">Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="0cb13-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0cb13-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="0cb13-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0cb13-105">Members</span></span>  
  
|<span data-ttu-id="0cb13-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0cb13-106">Member</span></span>|<span data-ttu-id="0cb13-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0cb13-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="0cb13-108">Przejście wynika z wywołania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="0cb13-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="0cb13-109">Przejście jest ze względu na powrót z funkcji.</span><span class="sxs-lookup"><span data-stu-id="0cb13-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cb13-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0cb13-110">Remarks</span></span>  
 <span data-ttu-id="0cb13-111">W przypadku przejścia profiler otrzymuje [icorprofilercallback::managedtounmanagedtransition —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) lub [icorprofilercallback::unmanagedtomanagedtransition —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) wywołanie zwrotne, które udostępnia wartość `COR_PRF_TRANSITION_REASON` wyliczenie, aby wskazać przyczynę przejścia.</span><span class="sxs-lookup"><span data-stu-id="0cb13-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb13-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0cb13-112">Requirements</span></span>  
 <span data-ttu-id="0cb13-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cb13-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb13-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0cb13-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0cb13-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cb13-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cb13-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cb13-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
