---
title: ICorProfilerObjectEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e8a623107e5e03ca36137c253c9bdf0a722d385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="c35b4-102">ICorProfilerObjectEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="c35b4-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="c35b4-103">Pobiera wskaźnika interfejsu kopię [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c35b4-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c35b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c35b4-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c35b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c35b4-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="c35b4-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię `ICorProfilerObjectEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c35b4-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="c35b4-107">Zachowuje własną stan wyliczenia, niezależnie od tego.</span><span class="sxs-lookup"><span data-stu-id="c35b4-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="c35b4-108">Jednak pozycji kursora początkowa kopia będzie taki sam jak ten moduł wyliczający bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="c35b4-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c35b4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c35b4-109">Requirements</span></span>  
 <span data-ttu-id="c35b4-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c35b4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c35b4-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c35b4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c35b4-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c35b4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c35b4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c35b4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c35b4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c35b4-114">See Also</span></span>  
 [<span data-ttu-id="c35b4-115">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="c35b4-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
