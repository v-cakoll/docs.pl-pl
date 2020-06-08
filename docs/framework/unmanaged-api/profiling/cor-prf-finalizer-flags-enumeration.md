---
title: COR_PRF_FINALIZER_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
ms.openlocfilehash: b273faafd7abb86ace58bb5c24473406af3ce20e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500978"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="ed790-102">COR_PRF_FINALIZER_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ed790-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="ed790-103">Opisuje finalizator dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="ed790-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed790-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed790-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="ed790-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ed790-105">Members</span></span>  
  
|<span data-ttu-id="ed790-106">Członek</span><span class="sxs-lookup"><span data-stu-id="ed790-106">Member</span></span>|<span data-ttu-id="ed790-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ed790-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="ed790-108">Finalizator jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ed790-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed790-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed790-109">Remarks</span></span>  
 <span data-ttu-id="ed790-110">`COR_PRF_FINALIZER_FLAGS`Wyliczenie jest używane przez metodę [ICorProfilerCallback2:: FinalizeableObjectQueued —](icorprofilercallback2-finalizeableobjectqueued-method.md) do opisywania finalizatora dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="ed790-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed790-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed790-111">Requirements</span></span>  
 <span data-ttu-id="ed790-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed790-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed790-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ed790-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed790-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed790-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed790-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed790-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed790-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed790-116">See also</span></span>

- [<span data-ttu-id="ed790-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ed790-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
