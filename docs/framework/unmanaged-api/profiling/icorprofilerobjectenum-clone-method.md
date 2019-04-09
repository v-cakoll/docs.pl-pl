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
ms.openlocfilehash: 14e8086532eff5dba6883575cc2daf447a32343a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182367"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="177c3-102">ICorProfilerObjectEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="177c3-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="177c3-103">Pobiera wskaźnik interfejsu do kopii tego [icorprofilerobjectenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="177c3-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="177c3-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="177c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="177c3-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="177c3-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię `ICorProfilerObjectEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="177c3-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="177c3-107">Zachowuje swój własny stan wyliczenia, niezależnie od niej.</span><span class="sxs-lookup"><span data-stu-id="177c3-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="177c3-108">Jednak pozycja kursora początkowa kopia będzie taki sam jak ten moduł wyliczający bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="177c3-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="177c3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="177c3-109">Requirements</span></span>  
 <span data-ttu-id="177c3-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="177c3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="177c3-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="177c3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="177c3-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="177c3-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="177c3-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="177c3-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="177c3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="177c3-114">See also</span></span>

- [<span data-ttu-id="177c3-115">ICorProfilerObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="177c3-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
