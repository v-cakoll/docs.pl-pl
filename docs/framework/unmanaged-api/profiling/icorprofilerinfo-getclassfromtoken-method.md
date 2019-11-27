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
ms.openlocfilehash: 6999821412b3cdd614cb30858a0616c9f27a6baa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448109"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="c71b2-102">ICorProfilerInfo::GetClassFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="c71b2-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="c71b2-103">Pobiera identyfikator klasy, z uwzględnieniem tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="c71b2-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="c71b2-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="c71b2-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c71b2-105">Zamiast tego użyj [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c71b2-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c71b2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c71b2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c71b2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c71b2-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="c71b2-108">podczas Identyfikator modułu, który zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="c71b2-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="c71b2-109">podczas `mdTypeDef` token metadanych, który odwołuje się do klasy.</span><span class="sxs-lookup"><span data-stu-id="c71b2-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="c71b2-110">określoną Wskaźnik do identyfikatora klasy.</span><span class="sxs-lookup"><span data-stu-id="c71b2-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c71b2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c71b2-111">Remarks</span></span>  
 <span data-ttu-id="c71b2-112">Ta metoda jest przestarzała; Zamiast tego należy używać `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="c71b2-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c71b2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c71b2-113">Requirements</span></span>  
 <span data-ttu-id="c71b2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c71b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c71b2-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c71b2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c71b2-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c71b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c71b2-117">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="c71b2-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71b2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c71b2-118">See also</span></span>

- [<span data-ttu-id="c71b2-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="c71b2-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
