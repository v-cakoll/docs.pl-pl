---
title: "ICorProfilerInfo::GetClassFromToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassFromToken
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 761c537f0b3aba529a8a3a862a1a975ddd1c6303
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="5a4c7-102">ICorProfilerInfo::GetClassFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a4c7-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="5a4c7-103">Pobiera identyfikator klasy, podany token metadanych.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="5a4c7-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5a4c7-105">Użyj [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4c7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a4c7-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a4c7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a4c7-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="5a4c7-108">[in] Identyfikator modułu, który zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="5a4c7-109">[in] `mdTypeDef` Token metadanych, który odwołuje się do klasy.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="5a4c7-110">[out] Wskaźnik do identyfikatora klasy.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a4c7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a4c7-111">Remarks</span></span>  
 <span data-ttu-id="5a4c7-112">Ta metoda jest przestarzała; Zamiast tego należy użyć `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a4c7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a4c7-113">Requirements</span></span>  
 <span data-ttu-id="5a4c7-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a4c7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a4c7-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a4c7-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a4c7-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a4c7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a4c7-117">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="5a4c7-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4c7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a4c7-118">See Also</span></span>  
 [<span data-ttu-id="5a4c7-119">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="5a4c7-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
