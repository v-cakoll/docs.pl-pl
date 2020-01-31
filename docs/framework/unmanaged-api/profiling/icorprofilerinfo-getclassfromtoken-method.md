---
title: ICorProfilerInfo::GetClassFromToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 841953625235406f013e9f140ad91c7b65680e47
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863956"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="c3fbd-102">ICorProfilerInfo::GetClassFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="c3fbd-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="c3fbd-103">Pobiera identyfikator klasy, z uwzględnieniem tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="c3fbd-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="c3fbd-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="c3fbd-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c3fbd-105">Zamiast tego użyj [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs —](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3fbd-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3fbd-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3fbd-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3fbd-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3fbd-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="c3fbd-108">podczas Identyfikator modułu, który zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="c3fbd-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="c3fbd-109">podczas `mdTypeDef` token metadanych, który odwołuje się do klasy.</span><span class="sxs-lookup"><span data-stu-id="c3fbd-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="c3fbd-110">określoną Wskaźnik do identyfikatora klasy.</span><span class="sxs-lookup"><span data-stu-id="c3fbd-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3fbd-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3fbd-111">Remarks</span></span>  
 <span data-ttu-id="c3fbd-112">Ta metoda jest przestarzała; Zamiast tego należy używać `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="c3fbd-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3fbd-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3fbd-113">Requirements</span></span>  
 <span data-ttu-id="c3fbd-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3fbd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3fbd-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c3fbd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3fbd-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c3fbd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3fbd-117">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="c3fbd-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3fbd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3fbd-118">See also</span></span>

- [<span data-ttu-id="c3fbd-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3fbd-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
