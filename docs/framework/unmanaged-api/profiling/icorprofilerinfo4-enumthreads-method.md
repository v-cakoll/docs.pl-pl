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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd0a4149b6dc6023579e8bc5b40751d23416e3a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683872"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="cd9e1-102">ICorProfilerInfo4::EnumThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd9e1-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="cd9e1-103">Zwraca moduł wyliczający, który udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji wszystkie zarządzane wątki w profilowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="cd9e1-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd9e1-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd9e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd9e1-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="cd9e1-106">[out] Wskaźnik do [icorprofilerthreadenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cd9e1-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd9e1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd9e1-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd9e1-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd9e1-108">Requirements</span></span>  
 <span data-ttu-id="cd9e1-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd9e1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd9e1-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd9e1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd9e1-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd9e1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd9e1-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd9e1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9e1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd9e1-113">See also</span></span>

- [<span data-ttu-id="cd9e1-114">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd9e1-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="cd9e1-115">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd9e1-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="cd9e1-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="cd9e1-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="cd9e1-117">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="cd9e1-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
