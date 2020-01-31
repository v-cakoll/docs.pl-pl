---
title: ICorProfilerInfo8, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 476bcbd91188e3ff9eb63f50cfa2118a440b1a69
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868320"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="66d9b-102">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="66d9b-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="66d9b-103">Podklasa elementu [ICorProfilerInfo7](icorprofilerinfo7-interface.md) , która dostarcza metody do badania informacji o metodach dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="66d9b-103">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="66d9b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="66d9b-104">Methods</span></span>  

| <span data-ttu-id="66d9b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="66d9b-105">Method</span></span>|<span data-ttu-id="66d9b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="66d9b-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="66d9b-107">IsFunctionDynamic, Metoda</span><span class="sxs-lookup"><span data-stu-id="66d9b-107">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="66d9b-108">Określa, czy funkcja nie ma skojarzonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="66d9b-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="66d9b-109">GetFunctionFromIP3, Metoda</span><span class="sxs-lookup"><span data-stu-id="66d9b-109">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="66d9b-110">Mapuje wskaźnik zarządzanej instrukcji kodu na FunctionID.</span><span class="sxs-lookup"><span data-stu-id="66d9b-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="66d9b-111">Ta metoda działa w przypadku metod dynamicznych i niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="66d9b-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="66d9b-112">GetDynamicFunctionInfo, Metoda</span><span class="sxs-lookup"><span data-stu-id="66d9b-112">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="66d9b-113">Pobiera informacje o metodach dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="66d9b-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="66d9b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66d9b-114">Requirements</span></span>  
<span data-ttu-id="66d9b-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66d9b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="66d9b-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="66d9b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="66d9b-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="66d9b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="66d9b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66d9b-118">See also</span></span>

- [<span data-ttu-id="66d9b-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="66d9b-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
