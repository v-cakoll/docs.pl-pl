---
title: "ICorProfilerThreadEnum::Clone — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d40ef6a9a666f06a46713c6295167cf5e0798ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="a36dd-102">ICorProfilerThreadEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="a36dd-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="a36dd-103">Pobiera wskaźnika interfejsu kopię [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a36dd-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a36dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a36dd-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a36dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a36dd-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a36dd-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a36dd-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="a36dd-107">Modułu wyliczającego zachowuje własną stan wyliczenia, niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="a36dd-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="a36dd-108">Jednak pozycji kursora początkowej kopii jest taki sam jak ten bieżącej pozycji kursora modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="a36dd-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a36dd-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a36dd-109">Requirements</span></span>  
 <span data-ttu-id="a36dd-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a36dd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a36dd-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a36dd-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a36dd-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a36dd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a36dd-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a36dd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a36dd-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a36dd-114">See Also</span></span>  
 [<span data-ttu-id="a36dd-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="a36dd-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="a36dd-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a36dd-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
