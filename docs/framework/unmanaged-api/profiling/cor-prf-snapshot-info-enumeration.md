---
title: "COR_PRF_SNAPSHOT_INFO — Wyliczenie"
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
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4573ec44253b1b0f26ae62591db149f0447d3935
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="4c0a1-102">COR_PRF_SNAPSHOT_INFO — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4c0a1-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="4c0a1-103">Określa, ile kopii danych do przekazania migawki stosu w każdym wywołaniu profilera [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="4c0a1-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c0a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c0a1-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="4c0a1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4c0a1-105">Members</span></span>  
  
|<span data-ttu-id="4c0a1-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4c0a1-106">Members</span></span>|<span data-ttu-id="4c0a1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4c0a1-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="4c0a1-108">Wskazuje, że wszystkie muszą być przekazywane wartości `StackSnapshotCallback` parametrów, z wyjątkiem `context` parametru.</span><span class="sxs-lookup"><span data-stu-id="4c0a1-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="4c0a1-109">Wskazuje, że wszystkie muszą być przekazywane wartości `StackSnapshotCallback` parametrów, takich jak `context` parametru.</span><span class="sxs-lookup"><span data-stu-id="4c0a1-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="4c0a1-110">Wskazuje, że będą używane jest prostsze, alternatywny przejście stosu algorytm.</span><span class="sxs-lookup"><span data-stu-id="4c0a1-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c0a1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c0a1-111">Remarks</span></span>  
 <span data-ttu-id="4c0a1-112">Wartości, które są udostępniane przez `COR_PRF_SNAPSHOT_INFO` wyliczenia są przekazywane jako parametry [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4c0a1-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c0a1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c0a1-113">Requirements</span></span>  
 <span data-ttu-id="4c0a1-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c0a1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c0a1-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c0a1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c0a1-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c0a1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c0a1-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c0a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0a1-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c0a1-118">See Also</span></span>  
 [<span data-ttu-id="4c0a1-119">DoStackSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="4c0a1-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="4c0a1-120">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4c0a1-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
