---
title: ICorProfilerInfo3::EnumModules — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be5d05c34272b9fa5755b4d0e22fa9094707c5ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093881"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="961b1-102">ICorProfilerInfo3::EnumModules — Metoda</span><span class="sxs-lookup"><span data-stu-id="961b1-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="961b1-103">Zwraca moduł wyliczający, który udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji modułów zarządzanych, które są ładowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="961b1-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="961b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="961b1-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="961b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="961b1-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="961b1-106">[out] Wskaźnik do [icorprofilermoduleenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="961b1-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="961b1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="961b1-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="961b1-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="961b1-108">Requirements</span></span>  
 <span data-ttu-id="961b1-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="961b1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="961b1-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="961b1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="961b1-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="961b1-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="961b1-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="961b1-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="961b1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="961b1-113">See also</span></span>

- [<span data-ttu-id="961b1-114">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="961b1-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="961b1-115">ICorProfilerInfo3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="961b1-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="961b1-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="961b1-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="961b1-117">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="961b1-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
