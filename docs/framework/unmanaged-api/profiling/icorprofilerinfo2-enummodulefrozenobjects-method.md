---
title: ICorProfilerInfo2::EnumModuleFrozenObjects — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a325c3e1aa9c08e00dc2cc38e3f7833fa9f99897
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472580"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="d20fe-102">ICorProfilerInfo2::EnumModuleFrozenObjects — Metoda</span><span class="sxs-lookup"><span data-stu-id="d20fe-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="d20fe-103">Pobiera moduł wyliczający, który pozwala iteracji przez zamrożone obiekty w określonym module. Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="d20fe-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d20fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d20fe-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d20fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d20fe-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="d20fe-106">[in] Identyfikator modułu, który zawiera zamrożonych obiektów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d20fe-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="d20fe-107">[out] Wskaźnik na adres [icorprofilerobjectenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interfejsu, który zawiera wyliczenie zamrożonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="d20fe-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d20fe-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d20fe-108">Requirements</span></span>  
 <span data-ttu-id="d20fe-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d20fe-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d20fe-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d20fe-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d20fe-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d20fe-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d20fe-112">**Wersje programu .NET framework:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span><span class="sxs-lookup"><span data-stu-id="d20fe-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d20fe-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d20fe-113">See also</span></span>
- [<span data-ttu-id="d20fe-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d20fe-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="d20fe-115">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d20fe-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
