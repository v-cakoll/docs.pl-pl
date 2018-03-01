---
title: "ICorProfilerInfo2::EnumModuleFrozenObjects — Metoda"
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
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3866d91d28258eaee78e6025175628796a369f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="5f5c8-102">ICorProfilerInfo2::EnumModuleFrozenObjects — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f5c8-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="5f5c8-103">Pobiera moduł wyliczający, który umożliwia iteracji za pośrednictwem zablokowane obiekty w ramach określonego modułu. Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="5f5c8-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f5c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f5c8-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f5c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f5c8-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="5f5c8-106">[in] Identyfikator modułu, który zawiera zablokowane obiekty, które mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="5f5c8-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="5f5c8-107">[out] Wskaźnik do adresu [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interfejs, który wylicza zablokowane obiekty.</span><span class="sxs-lookup"><span data-stu-id="5f5c8-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f5c8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f5c8-108">Requirements</span></span>  
 <span data-ttu-id="5f5c8-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f5c8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f5c8-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f5c8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f5c8-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f5c8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f5c8-112">**Wersje programu .NET framework:** 3.5, 3.0 z dodatkiem SP1, 3.0, 2.0 z dodatkiem SP1, 2.0</span><span class="sxs-lookup"><span data-stu-id="5f5c8-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5c8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f5c8-113">See Also</span></span>  
 [<span data-ttu-id="5f5c8-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f5c8-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="5f5c8-115">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f5c8-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
