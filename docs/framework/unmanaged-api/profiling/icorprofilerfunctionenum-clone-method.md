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
ms.openlocfilehash: ce5d5187ee4082bb851fa24bbcda2b099e37b89f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="490ea-102">ICorProfilerFunctionEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="490ea-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="490ea-103">Pobiera wskaźnika interfejsu kopię [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="490ea-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="490ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="490ea-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="490ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="490ea-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="490ea-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="490ea-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="490ea-107">Modułu wyliczającego zachowuje własną stan wyliczenia, niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="490ea-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="490ea-108">Jednak pozycji kursora początkowej kopii jest taki sam jak ten moduł wyliczający bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="490ea-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="490ea-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="490ea-109">Requirements</span></span>  
 <span data-ttu-id="490ea-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="490ea-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="490ea-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="490ea-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="490ea-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="490ea-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="490ea-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="490ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="490ea-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="490ea-114">See Also</span></span>  
 [<span data-ttu-id="490ea-115">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="490ea-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="490ea-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="490ea-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
