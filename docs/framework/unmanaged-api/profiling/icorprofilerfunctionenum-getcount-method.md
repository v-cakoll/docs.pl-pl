---
title: ICorProfilerFunctionEnum::GetCount — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 413b860353d3a9e75771f9349ebf151d8f2e3579
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453299"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="6e4f9-102">ICorProfilerFunctionEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="6e4f9-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="6e4f9-103">Pobiera liczbę funkcji, które zostały załadowane do aplikacji lub Wymuś załadowanych przez profiler.</span><span class="sxs-lookup"><span data-stu-id="6e4f9-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e4f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e4f9-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e4f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e4f9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6e4f9-106">[out] Liczba funkcji, które zostały załadowane.</span><span class="sxs-lookup"><span data-stu-id="6e4f9-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e4f9-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e4f9-107">Requirements</span></span>  
 <span data-ttu-id="6e4f9-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e4f9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e4f9-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e4f9-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e4f9-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e4f9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e4f9-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e4f9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4f9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e4f9-112">See Also</span></span>  
 [<span data-ttu-id="6e4f9-113">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="6e4f9-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="6e4f9-114">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="6e4f9-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
