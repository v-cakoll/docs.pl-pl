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
ms.openlocfilehash: 0301334621a2e393a59e7cc34f2964450a81213f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074173"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="db330-102">ICorProfilerThreadEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="db330-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="db330-103">Pobiera wskaźnik interfejsu do kopii tego [icorprofilerthreadenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db330-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db330-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db330-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db330-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db330-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="db330-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię [icorprofilerthreadenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db330-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="db330-107">Kopię moduł wyliczający zachowuje swój własny stan wyliczenia, niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="db330-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="db330-108">Jednak pozycji kursora początkowa kopia jest taka sama jak ta aktualną pozycją kursora modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="db330-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db330-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db330-109">Requirements</span></span>  
 <span data-ttu-id="db330-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db330-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db330-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="db330-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="db330-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db330-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db330-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db330-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db330-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db330-114">See also</span></span>

- [<span data-ttu-id="db330-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="db330-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="db330-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="db330-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
