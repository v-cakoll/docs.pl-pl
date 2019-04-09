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
ms.openlocfilehash: a5061750489c74e0385f2ce020c88518604b3167
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169289"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="a72c0-102">ICorProfilerFunctionEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="a72c0-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="a72c0-103">Pobiera liczbę funkcji, które zostały załadowane do aplikacji lub Wymuś ładowany przez program profilujący.</span><span class="sxs-lookup"><span data-stu-id="a72c0-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a72c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a72c0-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a72c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a72c0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a72c0-106">[out] Liczba funkcji, które zostały załadowane.</span><span class="sxs-lookup"><span data-stu-id="a72c0-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a72c0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a72c0-107">Requirements</span></span>  
 <span data-ttu-id="a72c0-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a72c0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a72c0-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a72c0-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a72c0-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a72c0-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a72c0-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a72c0-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a72c0-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a72c0-112">See also</span></span>

- [<span data-ttu-id="a72c0-113">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a72c0-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="a72c0-114">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a72c0-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
