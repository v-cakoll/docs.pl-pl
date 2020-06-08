---
title: ICorProfilerFunctionEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: d6f348eb781efdef89926ec1bc267281bf3a5004
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503110"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="3d4d6-102">ICorProfilerFunctionEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="3d4d6-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="3d4d6-103">Pobiera wskaźnik interfejsu do kopii tego interfejsu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3d4d6-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d4d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d4d6-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d4d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d4d6-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="3d4d6-106">określoną Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię tego interfejsu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3d4d6-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="3d4d6-107">Kopia modułu wyliczającego utrzymuje swój własny stan wyliczenia niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="3d4d6-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="3d4d6-108">Jednak początkowa pozycja kursora kopii jest taka sama jak pozycja bieżącego kursora tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="3d4d6-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d4d6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d4d6-109">Requirements</span></span>  
 <span data-ttu-id="3d4d6-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d4d6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d4d6-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3d4d6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d4d6-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3d4d6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d4d6-113">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d4d6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4d6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d4d6-114">See also</span></span>

- [<span data-ttu-id="3d4d6-115">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3d4d6-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="3d4d6-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3d4d6-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
