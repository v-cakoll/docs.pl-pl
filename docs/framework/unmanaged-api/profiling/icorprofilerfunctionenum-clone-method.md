---
title: "ICorProfilerFunctionEnum::Clone — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Clone Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dc1d14a1480c3634993190448f9beff911bebf6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="2bf08-102">ICorProfilerFunctionEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="2bf08-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="2bf08-103">Pobiera wskaźnika interfejsu kopię [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2bf08-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bf08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2bf08-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bf08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bf08-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2bf08-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2bf08-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="2bf08-107">Modułu wyliczającego zachowuje własną stan wyliczenia, niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="2bf08-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="2bf08-108">Jednak pozycji kursora początkowej kopii jest taki sam jak ten moduł wyliczający bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="2bf08-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bf08-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2bf08-109">Requirements</span></span>  
 <span data-ttu-id="2bf08-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bf08-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bf08-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2bf08-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2bf08-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bf08-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bf08-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bf08-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf08-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bf08-114">See Also</span></span>  
 [<span data-ttu-id="2bf08-115">ICorProfilerFunctionEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="2bf08-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="2bf08-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="2bf08-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
