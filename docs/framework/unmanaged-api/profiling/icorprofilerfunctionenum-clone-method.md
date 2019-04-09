---
title: ICorProfilerFunctionEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ffd1fcc36f0c6cc3c5f063c5a916e8918839566
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135593"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="999b8-102">ICorProfilerFunctionEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="999b8-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="999b8-103">Pobiera wskaźnik interfejsu do kopii tego [icorprofilerfunctionenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="999b8-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="999b8-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="999b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="999b8-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="999b8-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię [icorprofilerfunctionenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="999b8-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="999b8-107">Kopię moduł wyliczający zachowuje swój własny stan wyliczenia, niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="999b8-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="999b8-108">Jednak pozycja kursora początkowa kopia jest taki sam jak ten moduł wyliczający bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="999b8-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="999b8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="999b8-109">Requirements</span></span>  
 <span data-ttu-id="999b8-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="999b8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="999b8-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="999b8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="999b8-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="999b8-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="999b8-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="999b8-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="999b8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="999b8-114">See also</span></span>

- [<span data-ttu-id="999b8-115">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="999b8-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="999b8-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="999b8-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
