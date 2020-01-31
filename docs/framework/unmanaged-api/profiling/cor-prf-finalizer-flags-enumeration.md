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
ms.openlocfilehash: daca2849908a7798b588ff06f6e117d412db1b33
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867272"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="e3ea4-102">COR_PRF_FINALIZER_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e3ea4-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="e3ea4-103">Opisuje finalizator dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3ea4-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ea4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3ea4-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e3ea4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e3ea4-105">Members</span></span>  
  
|<span data-ttu-id="e3ea4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e3ea4-106">Member</span></span>|<span data-ttu-id="e3ea4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e3ea4-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="e3ea4-108">Finalizator jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e3ea4-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3ea4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3ea4-109">Remarks</span></span>  
 <span data-ttu-id="e3ea4-110">Wyliczenie `COR_PRF_FINALIZER_FLAGS` jest używane przez metodę [ICorProfilerCallback2:: FinalizeableObjectQueued —](icorprofilercallback2-finalizeableobjectqueued-method.md) do opisywania finalizatora dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3ea4-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3ea4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3ea4-111">Requirements</span></span>  
 <span data-ttu-id="e3ea4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3ea4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3ea4-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e3ea4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3ea4-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e3ea4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3ea4-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3ea4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ea4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3ea4-116">See also</span></span>

- [<span data-ttu-id="e3ea4-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e3ea4-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
