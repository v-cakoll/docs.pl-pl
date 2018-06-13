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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84a71ac3a1ba30e20bb6ec7e6a0e31db9d3b5738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455709"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="dfdc0-102">ICorProfilerThreadEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="dfdc0-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="dfdc0-103">Pobiera wskaźnika interfejsu kopię [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dfdc0-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfdc0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfdc0-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfdc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfdc0-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="dfdc0-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dfdc0-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="dfdc0-107">Modułu wyliczającego zachowuje własną stan wyliczenia, niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="dfdc0-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="dfdc0-108">Jednak pozycji kursora początkowej kopii jest taki sam jak ten bieżącej pozycji kursora modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="dfdc0-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfdc0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfdc0-109">Requirements</span></span>  
 <span data-ttu-id="dfdc0-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfdc0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfdc0-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dfdc0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dfdc0-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfdc0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfdc0-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfdc0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdc0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfdc0-114">See Also</span></span>  
 [<span data-ttu-id="dfdc0-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="dfdc0-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="dfdc0-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="dfdc0-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
