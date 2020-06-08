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
ms.openlocfilehash: 967f38add9ae5996c6ac33388203b55161a84e39
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498274"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="1b3a5-102">ICorProfilerInfo::GetILFunctionBodyAllocator — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b3a5-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="1b3a5-103">Pobiera interfejs, który zapewnia metodę przydzielenia pamięci, która ma zostać użyta do wymiany treści metody w kodzie języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="1b3a5-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b3a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b3a5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b3a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b3a5-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1b3a5-106">podczas Identyfikator modułu, w którym znajduje się ta metoda.</span><span class="sxs-lookup"><span data-stu-id="1b3a5-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="1b3a5-107">określoną Wskaźnik do interfejsu [IMethodMalloc](imethodmalloc-interface.md) , który zapewnia metodę przydzielenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="1b3a5-107">[out] A pointer to an [IMethodMalloc](imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b3a5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b3a5-108">Remarks</span></span>  
 <span data-ttu-id="1b3a5-109">Treść metody w kodzie MSIL musi znajdować się jako względny adres wirtualny (RVA) względem załadowanego modułu, co oznacza, że następuje po module w 4 GB.</span><span class="sxs-lookup"><span data-stu-id="1b3a5-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="1b3a5-110">Aby ułatwić narzędziu wymianę treści metody, `GetILFunctionBodyAllocator` Metoda zapewnia, że pamięć jest przypisana w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="1b3a5-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b3a5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b3a5-111">Requirements</span></span>  
 <span data-ttu-id="1b3a5-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b3a5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b3a5-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1b3a5-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b3a5-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1b3a5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b3a5-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b3a5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b3a5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b3a5-116">See also</span></span>

- [<span data-ttu-id="1b3a5-117">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b3a5-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
