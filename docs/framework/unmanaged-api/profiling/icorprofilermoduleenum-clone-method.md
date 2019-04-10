---
title: ICorProfilerModuleEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9053505f7356f4618993ead911f730909f53f383
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227148"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="71746-102">ICorProfilerModuleEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="71746-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="71746-103">Pobiera wskaźnik interfejsu do kopii tego [icorprofilermoduleenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="71746-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71746-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71746-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71746-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71746-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="71746-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię [icorprofilermoduleenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="71746-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="71746-107">Kopię moduł wyliczający zachowuje swój własny stan wyliczenia, niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="71746-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="71746-108">Jednak pozycja kursora początkowa kopia jest taki sam jak ten moduł wyliczający bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="71746-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71746-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71746-109">Requirements</span></span>  
 <span data-ttu-id="71746-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71746-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71746-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71746-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71746-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71746-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="71746-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="71746-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71746-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71746-114">See also</span></span>

- [<span data-ttu-id="71746-115">ICorProfilerModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="71746-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="71746-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="71746-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
