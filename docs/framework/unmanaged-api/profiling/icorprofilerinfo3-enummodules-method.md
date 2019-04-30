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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703559"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="4f1e1-102">ICorProfilerInfo3::EnumModules — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f1e1-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="4f1e1-103">Zwraca moduł wyliczający, który udostępnia metody umożliwiające sekwencyjnie iterowania po kolekcji modułów zarządzanych, które są ładowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f1e1-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f1e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f1e1-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f1e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f1e1-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="4f1e1-106">[out] Wskaźnik do [icorprofilermoduleenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4f1e1-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f1e1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f1e1-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f1e1-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f1e1-108">Requirements</span></span>  
 <span data-ttu-id="4f1e1-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f1e1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f1e1-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f1e1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f1e1-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f1e1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f1e1-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f1e1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1e1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f1e1-113">See also</span></span>

- [<span data-ttu-id="4f1e1-114">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f1e1-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="4f1e1-115">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f1e1-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="4f1e1-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="4f1e1-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4f1e1-117">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="4f1e1-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
