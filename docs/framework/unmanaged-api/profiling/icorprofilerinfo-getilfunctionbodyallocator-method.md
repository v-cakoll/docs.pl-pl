---
title: ICorProfilerInfo::GetILFunctionBodyAllocator — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2cd66a895f99d62e8deaa45afab12d963aee2901
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109125"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="9c47f-102">ICorProfilerInfo::GetILFunctionBodyAllocator — Metoda</span><span class="sxs-lookup"><span data-stu-id="9c47f-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="9c47f-103">Pobiera interfejs, który udostępnia metodę, aby przydzielić pamięć do użytku z zastępowaniu treści metody w kodzie języka intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9c47f-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c47f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c47f-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c47f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c47f-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="9c47f-106">[in] Identyfikator modułu, w której znajduje się metody.</span><span class="sxs-lookup"><span data-stu-id="9c47f-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="9c47f-107">[out] Wskaźnik do [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interfejs, który udostępnia metodę w celu przydzielenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="9c47f-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c47f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c47f-108">Remarks</span></span>  
 <span data-ttu-id="9c47f-109">Treści metody w kodzie MSIL muszą znajdować się jako względnych adresów wirtualnych (RVA) względem załadowanym module, co oznacza, że jest zgodna z modułu w 4 GB.</span><span class="sxs-lookup"><span data-stu-id="9c47f-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="9c47f-110">Aby ułatwić narzędzie wymienić treści metody `GetILFunctionBodyAllocator` metoda zapewnia, że pamięć jest przydzielany w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="9c47f-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c47f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c47f-111">Requirements</span></span>  
 <span data-ttu-id="9c47f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c47f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c47f-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9c47f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c47f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c47f-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9c47f-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9c47f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9c47f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c47f-116">See also</span></span>

- [<span data-ttu-id="9c47f-117">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9c47f-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
