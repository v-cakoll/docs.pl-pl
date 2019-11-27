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
ms.openlocfilehash: 5e718d05f033cc46fa460a81f6816a13ec32476d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428350"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="56f50-102">COR_PRF_FINALIZER_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="56f50-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="56f50-103">Opisuje finalizator dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="56f50-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f50-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56f50-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="56f50-105">Members</span><span class="sxs-lookup"><span data-stu-id="56f50-105">Members</span></span>  
  
|<span data-ttu-id="56f50-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="56f50-106">Member</span></span>|<span data-ttu-id="56f50-107">Opis</span><span class="sxs-lookup"><span data-stu-id="56f50-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="56f50-108">Finalizator jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="56f50-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56f50-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56f50-109">Remarks</span></span>  
 <span data-ttu-id="56f50-110">Wyliczenie `COR_PRF_FINALIZER_FLAGS` jest używane przez metodę [ICorProfilerCallback2:: FinalizeableObjectQueued —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) do opisywania finalizatora dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="56f50-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f50-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56f50-111">Requirements</span></span>  
 <span data-ttu-id="56f50-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f50-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f50-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="56f50-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56f50-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="56f50-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56f50-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56f50-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f50-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56f50-116">See also</span></span>

- [<span data-ttu-id="56f50-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="56f50-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
