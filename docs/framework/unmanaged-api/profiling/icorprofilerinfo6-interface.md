---
title: ICorProfilerInfo6, interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53120508c4810270747f749f1adfbae6ba800404
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567896"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="a3fb2-102">ICorProfilerInfo6, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3fb2-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="a3fb2-103">[Obsługiwane w programie .NET Framework 4.6 lub nowszy]</span><span class="sxs-lookup"><span data-stu-id="a3fb2-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="a3fb2-104">Podklasa klasy [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) , dostarcza moduł wyliczający dla wszystkich metod, które są zdefiniowane w danym module NGen i wbudowane danej metody.</span><span class="sxs-lookup"><span data-stu-id="a3fb2-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3fb2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a3fb2-105">Methods</span></span>  
  
|<span data-ttu-id="a3fb2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a3fb2-106">Method</span></span>|<span data-ttu-id="a3fb2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a3fb2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3fb2-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="a3fb2-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="a3fb2-109">Zwraca moduł wyliczający dla wszystkich metod należących do danego modułu NGen i są śródwierszowe w treści danej metody.</span><span class="sxs-lookup"><span data-stu-id="a3fb2-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3fb2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3fb2-110">Requirements</span></span>  
 <span data-ttu-id="a3fb2-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3fb2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3fb2-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3fb2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3fb2-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3fb2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3fb2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3fb2-114">See also</span></span>
- [<span data-ttu-id="a3fb2-115">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a3fb2-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
