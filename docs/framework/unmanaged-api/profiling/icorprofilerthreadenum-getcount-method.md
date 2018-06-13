---
title: ICorProfilerThreadEnum::GetCount — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b803c83b905df47b3957e07c0d64e7ce6f6d303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455481"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="d4f01-102">ICorProfilerThreadEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4f01-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="d4f01-103">Pobiera liczbę wątków, które są używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d4f01-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4f01-104">Syntax</span></span>  
  
```  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4f01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4f01-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d4f01-106">[out] Liczba wątków używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d4f01-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4f01-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4f01-107">Requirements</span></span>  
 <span data-ttu-id="d4f01-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4f01-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4f01-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4f01-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4f01-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4f01-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4f01-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4f01-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f01-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4f01-112">See Also</span></span>  
 [<span data-ttu-id="d4f01-113">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4f01-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="d4f01-114">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d4f01-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
