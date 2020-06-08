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
ms.openlocfilehash: d42c86a458661d3559f99235a6d5b208c82d1963
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502811"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="60c17-102">ICorProfilerInfo4::EnumThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="60c17-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="60c17-103">Zwraca moduł wyliczający, który dostarcza metody sekwencyjnie iteracji przez kolekcję wszystkich zarządzanych wątków w profilowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="60c17-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60c17-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60c17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60c17-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="60c17-106">określoną Wskaźnik do interfejsu [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="60c17-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60c17-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60c17-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60c17-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60c17-108">Requirements</span></span>  
 <span data-ttu-id="60c17-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60c17-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60c17-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="60c17-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60c17-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="60c17-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60c17-112">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60c17-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c17-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60c17-113">See also</span></span>

- [<span data-ttu-id="60c17-114">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="60c17-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="60c17-115">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="60c17-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="60c17-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="60c17-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="60c17-117">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="60c17-117">Profiling</span></span>](index.md)
