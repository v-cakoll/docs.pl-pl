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
ms.openlocfilehash: 8153dbd27e168e3a5bd8e5aeada955a0382aaf75
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868255"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="a68d7-102">ICorProfilerObjectEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="a68d7-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="a68d7-103">Pobiera wskaźnik interfejsu do kopii tego interfejsu [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a68d7-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a68d7-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a68d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a68d7-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a68d7-106">określoną Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię tego interfejsu `ICorProfilerObjectEnum`.</span><span class="sxs-lookup"><span data-stu-id="a68d7-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="a68d7-107">Kopia zachowuje swój własny stan wyliczenia niezależnie od tego.</span><span class="sxs-lookup"><span data-stu-id="a68d7-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="a68d7-108">Jednak początkowa pozycja kursora kopii będzie taka sama jak pozycja bieżącego kursora tego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="a68d7-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a68d7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a68d7-109">Requirements</span></span>  
 <span data-ttu-id="a68d7-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a68d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a68d7-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a68d7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a68d7-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a68d7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a68d7-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a68d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68d7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a68d7-114">See also</span></span>

- [<span data-ttu-id="a68d7-115">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a68d7-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
