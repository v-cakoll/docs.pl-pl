---
title: ICorProfilerFunctionEnum::GetCount — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: 5ccd90e92e83d7f9f6f19a082fb84dc1f1c35f4c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447808"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="dc8fe-102">ICorProfilerFunctionEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="dc8fe-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="dc8fe-103">Pobiera liczbę funkcji, które zostały załadowane przez aplikację lub wymuszanie załadowane przez profiler.</span><span class="sxs-lookup"><span data-stu-id="dc8fe-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc8fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc8fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc8fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc8fe-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="dc8fe-106">określoną Liczba załadowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="dc8fe-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc8fe-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc8fe-107">Requirements</span></span>  
 <span data-ttu-id="dc8fe-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc8fe-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc8fe-109">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dc8fe-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc8fe-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dc8fe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc8fe-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc8fe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc8fe-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc8fe-112">See also</span></span>

- [<span data-ttu-id="dc8fe-113">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc8fe-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="dc8fe-114">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="dc8fe-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
