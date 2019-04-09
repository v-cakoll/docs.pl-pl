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
ms.openlocfilehash: d5037f335e8d66c341d70d91d955a1ac7571b823
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123763"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="c8f39-102">COR_PRF_FINALIZER_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8f39-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="c8f39-103">W tym artykule opisano finalizatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="c8f39-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8f39-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c8f39-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c8f39-105">Members</span></span>  
  
|<span data-ttu-id="c8f39-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c8f39-106">Member</span></span>|<span data-ttu-id="c8f39-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f39-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="c8f39-108">Finalizator ma kluczowe znaczenie.</span><span class="sxs-lookup"><span data-stu-id="c8f39-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8f39-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8f39-109">Remarks</span></span>  
 <span data-ttu-id="c8f39-110">`COR_PRF_FINALIZER_FLAGS` Wyliczenie jest używane przez [icorprofilercallback2::finalizeableobjectqueued —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) metody do opisania finalizatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="c8f39-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8f39-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8f39-111">Requirements</span></span>  
 <span data-ttu-id="c8f39-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8f39-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8f39-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c8f39-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c8f39-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8f39-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c8f39-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c8f39-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8f39-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8f39-116">See also</span></span>

- [<span data-ttu-id="c8f39-117">Profilowanie — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c8f39-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
