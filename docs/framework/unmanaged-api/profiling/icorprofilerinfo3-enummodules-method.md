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
ms.openlocfilehash: 85adf2dbdbb8c02192a9017bc4f664274a08ee24
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496584"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="cda99-102">ICorProfilerInfo3::EnumModules — Metoda</span><span class="sxs-lookup"><span data-stu-id="cda99-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="cda99-103">Zwraca moduł wyliczający, który dostarcza metody sekwencyjnie iteracji przez kolekcję modułów zarządzanych, które są ładowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cda99-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda99-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cda99-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cda99-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cda99-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="cda99-106">określoną Wskaźnik do interfejsu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cda99-106">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cda99-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cda99-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cda99-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cda99-108">Requirements</span></span>  
 <span data-ttu-id="cda99-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cda99-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda99-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cda99-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cda99-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cda99-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cda99-112">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cda99-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda99-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cda99-113">See also</span></span>

- [<span data-ttu-id="cda99-114">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cda99-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="cda99-115">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="cda99-115">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="cda99-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="cda99-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cda99-117">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="cda99-117">Profiling</span></span>](index.md)
