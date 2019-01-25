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
ms.openlocfilehash: 12524de994264d83abf5b5338654e89a0964adff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667703"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="2e8cd-102">ICorProfilerInfo::GetClassFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e8cd-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="2e8cd-103">Pobiera identyfikator klasy, biorąc pod uwagę token metadanych.</span><span class="sxs-lookup"><span data-stu-id="2e8cd-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="2e8cd-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="2e8cd-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="2e8cd-105">Użyj [icorprofilerinfo2::getclassfromtokenandtypeargs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="2e8cd-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e8cd-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e8cd-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e8cd-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e8cd-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="2e8cd-108">[in] Identyfikator modułu, który zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="2e8cd-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="2e8cd-109">[in] `mdTypeDef` Token metadanych, który odwołuje się do klasy.</span><span class="sxs-lookup"><span data-stu-id="2e8cd-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="2e8cd-110">[out] Wskaźnik do identyfikator klasy.</span><span class="sxs-lookup"><span data-stu-id="2e8cd-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e8cd-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e8cd-111">Remarks</span></span>  
 <span data-ttu-id="2e8cd-112">Ta metoda jest przestarzała; Zamiast tego należy użyć `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="2e8cd-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e8cd-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e8cd-113">Requirements</span></span>  
 <span data-ttu-id="2e8cd-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e8cd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e8cd-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2e8cd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e8cd-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e8cd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e8cd-117">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="2e8cd-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8cd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e8cd-118">See also</span></span>
- [<span data-ttu-id="2e8cd-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e8cd-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
