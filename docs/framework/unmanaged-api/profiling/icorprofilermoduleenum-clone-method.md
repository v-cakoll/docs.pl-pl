---
title: ICorProfilerModuleEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: ccbb051ac30fb25199ce12c16fff74bb0b9944fa
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495089"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="35870-102">ICorProfilerModuleEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="35870-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="35870-103">Pobiera wskaźnik interfejsu do kopii tego interfejsu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="35870-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35870-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35870-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35870-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35870-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="35870-106">określoną Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię tego interfejsu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="35870-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="35870-107">Kopia modułu wyliczającego utrzymuje swój własny stan wyliczenia niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="35870-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="35870-108">Jednak początkowa pozycja kursora kopii jest taka sama jak pozycja bieżącego kursora tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="35870-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35870-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35870-109">Requirements</span></span>  
 <span data-ttu-id="35870-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35870-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35870-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="35870-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35870-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="35870-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35870-113">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35870-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35870-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35870-114">See also</span></span>

- [<span data-ttu-id="35870-115">ICorProfilerModuleEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="35870-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="35870-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="35870-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
