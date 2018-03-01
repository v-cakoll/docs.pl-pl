---
title: "ICorProfilerObjectEnum::Clone — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d8e478eb9165b4aa5bf019f02f4f128931d928b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="5d36c-102">ICorProfilerObjectEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="5d36c-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="5d36c-103">Pobiera wskaźnika interfejsu kopię [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5d36c-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d36c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d36c-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d36c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d36c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5d36c-106">[out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię `ICorProfilerObjectEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5d36c-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="5d36c-107">Zachowuje własną stan wyliczenia, niezależnie od tego.</span><span class="sxs-lookup"><span data-stu-id="5d36c-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="5d36c-108">Jednak pozycji kursora początkowa kopia będzie taki sam jak ten moduł wyliczający bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="5d36c-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d36c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d36c-109">Requirements</span></span>  
 <span data-ttu-id="5d36c-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d36c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d36c-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d36c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d36c-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d36c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d36c-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d36c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d36c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d36c-114">See Also</span></span>  
 [<span data-ttu-id="5d36c-115">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="5d36c-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
