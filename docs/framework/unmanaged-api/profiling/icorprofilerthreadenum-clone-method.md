---
title: ICorProfilerThreadEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
ms.openlocfilehash: ca29655d1d0eb819dfe8b5f9910cd20ef47843c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441528"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="8a970-102">ICorProfilerThreadEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a970-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="8a970-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="8a970-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a970-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a970-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a970-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a970-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="8a970-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="8a970-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="8a970-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span><span class="sxs-lookup"><span data-stu-id="8a970-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="8a970-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span><span class="sxs-lookup"><span data-stu-id="8a970-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a970-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a970-109">Requirements</span></span>  
 <span data-ttu-id="8a970-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a970-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a970-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a970-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a970-112">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a970-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a970-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a970-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a970-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a970-114">See also</span></span>

- [<span data-ttu-id="8a970-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="8a970-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="8a970-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="8a970-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
