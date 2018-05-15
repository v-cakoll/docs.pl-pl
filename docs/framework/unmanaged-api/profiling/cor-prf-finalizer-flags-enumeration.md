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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9292e7c5908b2e4fd7e2c0ae9412375249f2fdfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="3e30b-102">COR_PRF_FINALIZER_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3e30b-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="3e30b-103">W tym artykule opisano finalizatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="3e30b-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e30b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e30b-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="3e30b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3e30b-105">Members</span></span>  
  
|<span data-ttu-id="3e30b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3e30b-106">Member</span></span>|<span data-ttu-id="3e30b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3e30b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="3e30b-108">Bardzo ważne jest finalizatora.</span><span class="sxs-lookup"><span data-stu-id="3e30b-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e30b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e30b-109">Remarks</span></span>  
 <span data-ttu-id="3e30b-110">`COR_PRF_FINALIZER_FLAGS` Wyliczenie jest używany przez [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) metody do opisywania finalizatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="3e30b-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e30b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e30b-111">Requirements</span></span>  
 <span data-ttu-id="3e30b-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e30b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e30b-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3e30b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3e30b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e30b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e30b-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e30b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e30b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e30b-116">See Also</span></span>  
 [<span data-ttu-id="3e30b-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3e30b-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
