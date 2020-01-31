---
title: COR_PRF_SNAPSHOT_INFO — Wyliczenie
ms.date: 03/30/2017
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
ms.openlocfilehash: 97bf3e69a8ea155d53479ba6f61988e56e3bd396
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867027"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="343b5-102">COR_PRF_SNAPSHOT_INFO — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="343b5-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="343b5-103">Określa ilość danych, które mają zostać przekazane z migawki stosu w każdym wywołaniu funkcji [StackSnapshotCallback —](stacksnapshotcallback-function.md) profilera.</span><span class="sxs-lookup"><span data-stu-id="343b5-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="343b5-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="343b5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="343b5-105">Members</span></span>  
  
|<span data-ttu-id="343b5-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="343b5-106">Members</span></span>|<span data-ttu-id="343b5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="343b5-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="343b5-108">Wskazuje, że należy przesłać wartości dla wszystkich parametrów `StackSnapshotCallback`, z wyjątkiem parametru `context`.</span><span class="sxs-lookup"><span data-stu-id="343b5-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="343b5-109">Wskazuje, że należy przesłać wartości dla wszystkich parametrów `StackSnapshotCallback`, łącznie z parametrem `context`.</span><span class="sxs-lookup"><span data-stu-id="343b5-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="343b5-110">Wskazuje, że zostanie użyty prostszy, alternatywny algorytm przechodzenia stosu.</span><span class="sxs-lookup"><span data-stu-id="343b5-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="343b5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="343b5-111">Remarks</span></span>  
 <span data-ttu-id="343b5-112">Wartości, które są dostarczane przez Wyliczenie `COR_PRF_SNAPSHOT_INFO` są przekazywane jako parametry do metody [DoStackSnapshot —](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="343b5-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="343b5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="343b5-113">Requirements</span></span>  
 <span data-ttu-id="343b5-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="343b5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="343b5-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="343b5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="343b5-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="343b5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="343b5-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="343b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343b5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="343b5-118">See also</span></span>

- [<span data-ttu-id="343b5-119">DoStackSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="343b5-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="343b5-120">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="343b5-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
