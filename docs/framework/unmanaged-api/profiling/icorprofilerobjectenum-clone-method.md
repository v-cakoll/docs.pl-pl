---
title: ICorProfilerObjectEnum::Clone — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: a2a54c32c0713b4b69d8f2a0272687cbe9420610
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494777"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="fcbb8-102">ICorProfilerObjectEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="fcbb8-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="fcbb8-103">Pobiera wskaźnik interfejsu do kopii tego interfejsu [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fcbb8-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcbb8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcbb8-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcbb8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcbb8-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="fcbb8-106">określoną Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię tego `ICorProfilerObjectEnum` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fcbb8-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="fcbb8-107">Kopia zachowuje swój własny stan wyliczenia niezależnie od tego.</span><span class="sxs-lookup"><span data-stu-id="fcbb8-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="fcbb8-108">Jednak początkowa pozycja kursora kopii będzie taka sama jak pozycja bieżącego kursora tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="fcbb8-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbb8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fcbb8-109">Requirements</span></span>  
 <span data-ttu-id="fcbb8-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcbb8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcbb8-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fcbb8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fcbb8-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fcbb8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcbb8-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcbb8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbb8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcbb8-114">See also</span></span>

- [<span data-ttu-id="fcbb8-115">ICorProfilerObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fcbb8-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
