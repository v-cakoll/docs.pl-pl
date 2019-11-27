---
title: ICorProfilerInfo4::EnumThreads — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: d6af5aec4f1a012b6ec33cf80b1de62a7397262d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442987"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="4d39b-102">ICorProfilerInfo4::EnumThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d39b-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="4d39b-103">Zwraca moduł wyliczający, który dostarcza metody sekwencyjnie iteracji przez kolekcję wszystkich zarządzanych wątków w profilowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="4d39b-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d39b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d39b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d39b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d39b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="4d39b-106">określoną Wskaźnik do interfejsu [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4d39b-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d39b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d39b-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d39b-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d39b-108">Requirements</span></span>  
 <span data-ttu-id="4d39b-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d39b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d39b-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4d39b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d39b-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4d39b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d39b-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d39b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d39b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d39b-113">See also</span></span>

- [<span data-ttu-id="4d39b-114">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d39b-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="4d39b-115">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d39b-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="4d39b-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="4d39b-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4d39b-117">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="4d39b-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
