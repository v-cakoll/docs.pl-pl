---
title: ICorProfilerInfo::SetILFunctionBody — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abe0a0fc177c9ec89f4621e7defb5330c911034b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778620"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="45e66-102">ICorProfilerInfo::SetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="45e66-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="45e66-103">Zastępuje treść określonej funkcji w określonym module.</span><span class="sxs-lookup"><span data-stu-id="45e66-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45e66-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45e66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45e66-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="45e66-106">[in] Identyfikator modułu, w której znajduje się funkcja.</span><span class="sxs-lookup"><span data-stu-id="45e66-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="45e66-107">[in] Token funkcji, do których chcesz zastąpić treści.</span><span class="sxs-lookup"><span data-stu-id="45e66-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="45e66-108">[in] Nowy nagłówek dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="45e66-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45e66-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45e66-109">Remarks</span></span>  
 <span data-ttu-id="45e66-110">`SetILFunctionBody` Metoda zastępuje wirtualny adres względny funkcji w metadanych, które wskazuje na nowych treści funkcji oraz dostosowuje wszelkich struktur danych wewnętrznych, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="45e66-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="45e66-111">`SetILFunctionBody` Metodę można wywołać tylko funkcje, które nigdy nie zostały skompilowane przez kompilator just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="45e66-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="45e66-112">Użyj [icorprofilerinfo::getilfunctionbodyallocator —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) metodę, aby przydzielić miejsce dla nowej metody upewnić się, że rozmiar buforu jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="45e66-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e66-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45e66-113">Requirements</span></span>  
 <span data-ttu-id="45e66-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e66-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e66-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45e66-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45e66-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45e66-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45e66-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e66-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e66-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45e66-118">See also</span></span>

- [<span data-ttu-id="45e66-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="45e66-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
