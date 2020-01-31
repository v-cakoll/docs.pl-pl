---
title: ICorProfilerThreadEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
ms.openlocfilehash: 9048d314404859a4264621a5da91c43c525027f9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868203"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="29e43-102">ICorProfilerThreadEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="29e43-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="29e43-103">Pobiera wskaźnik interfejsu do kopii tego interfejsu [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="29e43-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29e43-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29e43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29e43-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="29e43-106">określoną Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię tego interfejsu [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="29e43-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="29e43-107">Kopia modułu wyliczającego utrzymuje swój własny stan wyliczenia niezależnie od tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="29e43-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="29e43-108">Jednak początkowa pozycja kursora kopii jest taka sama, jak bieżąca pozycja kursora modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="29e43-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e43-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29e43-109">Requirements</span></span>  
 <span data-ttu-id="29e43-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29e43-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29e43-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="29e43-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29e43-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="29e43-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29e43-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29e43-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e43-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29e43-114">See also</span></span>

- [<span data-ttu-id="29e43-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="29e43-115">ICorProfilerThreadEnum</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="29e43-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="29e43-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
