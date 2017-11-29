---
title: "ICorProfilerInfo::GetILFunctionBodyAllocator — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBodyAllocator
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45a50fc39f2df9d4998f8490ff4382c84c5aa9bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="1438a-102">ICorProfilerInfo::GetILFunctionBodyAllocator — Metoda</span><span class="sxs-lookup"><span data-stu-id="1438a-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="1438a-103">Pobiera interfejs, który udostępnia metody można przydzielić pamięci do zastosowania w przypadku zastępowaniu treści metody w kodzie języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1438a-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1438a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1438a-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1438a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1438a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1438a-106">[in] Identyfikator modułu, w której znajduje się metody.</span><span class="sxs-lookup"><span data-stu-id="1438a-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="1438a-107">[out] Wskaźnik do [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interfejs, który udostępnia metody przydzielić pamięci.</span><span class="sxs-lookup"><span data-stu-id="1438a-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1438a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1438a-108">Remarks</span></span>  
 <span data-ttu-id="1438a-109">Treści metody w kodzie MSIL musi znajdować się jako wirtualnego adresu względnego (RVA) względem załadować modułu, co oznacza, że jest on zgodny moduł w 4 GB.</span><span class="sxs-lookup"><span data-stu-id="1438a-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="1438a-110">Aby ułatwić narzędzia wymienić treści metody, `GetILFunctionBodyAllocator` — metoda gwarantuje, że pamięć jest przydzielona w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="1438a-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1438a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1438a-111">Requirements</span></span>  
 <span data-ttu-id="1438a-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1438a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1438a-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1438a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1438a-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1438a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1438a-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1438a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1438a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1438a-116">See Also</span></span>  
 [<span data-ttu-id="1438a-117">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="1438a-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
