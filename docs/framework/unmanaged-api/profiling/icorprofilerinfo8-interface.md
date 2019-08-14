---
title: ICorProfilerInfo8, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 210029ed1b1c7d780f3895f975f7a72227bbea80
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973694"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="3c0d0-102">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c0d0-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="3c0d0-103">Podklasa elementu [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) , która dostarcza metody do badania informacji o metodach dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="3c0d0-103">A subclass of [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="3c0d0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3c0d0-104">Methods</span></span>  

| <span data-ttu-id="3c0d0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3c0d0-105">Method</span></span>|<span data-ttu-id="3c0d0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3c0d0-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="3c0d0-107">IsFunctionDynamic, Metoda</span><span class="sxs-lookup"><span data-stu-id="3c0d0-107">IsFunctionDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="3c0d0-108">Określa, czy funkcja nie ma skojarzonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="3c0d0-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="3c0d0-109">GetFunctionFromIP3, Metoda</span><span class="sxs-lookup"><span data-stu-id="3c0d0-109">GetFunctionFromIP3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="3c0d0-110">Mapuje wskaźnik zarządzanej instrukcji kodu na FunctionID.</span><span class="sxs-lookup"><span data-stu-id="3c0d0-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="3c0d0-111">Ta metoda działa w przypadku metod dynamicznych i niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="3c0d0-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="3c0d0-112">GetDynamicFunctionInfo, Metoda</span><span class="sxs-lookup"><span data-stu-id="3c0d0-112">GetDynamicFunctionInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="3c0d0-113">Pobiera informacje o metodach dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="3c0d0-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="3c0d0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c0d0-114">Requirements</span></span>  
<span data-ttu-id="3c0d0-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c0d0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3c0d0-116">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3c0d0-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="3c0d0-117">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3c0d0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
## <a name="see-also"></a><span data-ttu-id="3c0d0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c0d0-118">See also</span></span>
- [<span data-ttu-id="3c0d0-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3c0d0-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
