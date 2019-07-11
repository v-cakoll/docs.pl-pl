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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6403540f9641ce885edf2760370e35f48faf1f10
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780318"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="400d2-102">ICorProfilerFunctionEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="400d2-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="400d2-103">Pobiera liczbę funkcji, które zostały załadowane do aplikacji lub Wymuś ładowany przez program profilujący.</span><span class="sxs-lookup"><span data-stu-id="400d2-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="400d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="400d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="400d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="400d2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="400d2-106">[out] Liczba funkcji, które zostały załadowane.</span><span class="sxs-lookup"><span data-stu-id="400d2-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="400d2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="400d2-107">Requirements</span></span>  
 <span data-ttu-id="400d2-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="400d2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="400d2-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="400d2-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="400d2-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="400d2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="400d2-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="400d2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="400d2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="400d2-112">See also</span></span>

- [<span data-ttu-id="400d2-113">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="400d2-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="400d2-114">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="400d2-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
