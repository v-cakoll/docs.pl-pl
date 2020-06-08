---
title: ICorProfilerInfo2::EnumModuleFrozenObjects — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: 1fe44f8f84c079e920c8c82fb9d52d1980d3b852
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497208"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="6fe9a-102">ICorProfilerInfo2::EnumModuleFrozenObjects — Metoda</span><span class="sxs-lookup"><span data-stu-id="6fe9a-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="6fe9a-103">Pobiera moduł wyliczający, który umożliwia iterację w odniesieniu do zablokowanych obiektów w określonym module. Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="6fe9a-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fe9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fe9a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fe9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fe9a-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="6fe9a-106">podczas Identyfikator modułu zawierającego zamrożone obiekty, które mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="6fe9a-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="6fe9a-107">określoną Wskaźnik do adresu interfejsu [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) , który wylicza zamrożone obiekty.</span><span class="sxs-lookup"><span data-stu-id="6fe9a-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fe9a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6fe9a-108">Requirements</span></span>  
 <span data-ttu-id="6fe9a-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fe9a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fe9a-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6fe9a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6fe9a-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6fe9a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fe9a-112">**.NET Framework wersje:** 3,5, 3,0 sp1, 3,0, 2,0 SP1, 2,0</span><span class="sxs-lookup"><span data-stu-id="6fe9a-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe9a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fe9a-113">See also</span></span>

- [<span data-ttu-id="6fe9a-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="6fe9a-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="6fe9a-115">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6fe9a-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
