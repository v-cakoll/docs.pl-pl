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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 580c554c968819ba4ef2ba52edeb5e754d33ac1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991903"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="6eeff-102">ICorProfilerInfo::GetClassFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="6eeff-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="6eeff-103">Pobiera identyfikator klasy, biorąc pod uwagę token metadanych.</span><span class="sxs-lookup"><span data-stu-id="6eeff-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="6eeff-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="6eeff-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6eeff-105">Użyj [icorprofilerinfo2::getclassfromtokenandtypeargs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="6eeff-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eeff-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6eeff-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eeff-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eeff-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="6eeff-108">[in] Identyfikator modułu, który zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="6eeff-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="6eeff-109">[in] `mdTypeDef` Token metadanych, który odwołuje się do klasy.</span><span class="sxs-lookup"><span data-stu-id="6eeff-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="6eeff-110">[out] Wskaźnik do identyfikator klasy.</span><span class="sxs-lookup"><span data-stu-id="6eeff-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eeff-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6eeff-111">Remarks</span></span>  
 <span data-ttu-id="6eeff-112">Ta metoda jest przestarzała; Zamiast tego należy użyć `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="6eeff-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eeff-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6eeff-113">Requirements</span></span>  
 <span data-ttu-id="6eeff-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eeff-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eeff-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6eeff-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6eeff-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6eeff-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6eeff-117">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="6eeff-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eeff-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6eeff-118">See also</span></span>

- [<span data-ttu-id="6eeff-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="6eeff-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
