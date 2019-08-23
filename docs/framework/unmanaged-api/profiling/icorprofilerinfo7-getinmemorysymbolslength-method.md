---
title: 'ICorProfilerInfo7:: GetInMemorySymbolsLength, Metoda'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 157b0e215f8afa58cccb3d54a65baa9c307ba966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955426"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="f705b-102">ICorProfilerInfo7:: GetInMemorySymbolsLength, Metoda</span><span class="sxs-lookup"><span data-stu-id="f705b-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="f705b-103">[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="f705b-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="f705b-104">Zwraca długość strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f705b-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f705b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f705b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f705b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f705b-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f705b-107">podczas Identyfikator modułu zawierającego strumień znajdujący się w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f705b-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="f705b-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="f705b-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="f705b-109">określoną Wskaźnik do `DWORD` wartości, która, gdy zwraca metodę, zawiera długość strumienia w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f705b-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f705b-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f705b-110">Return Value</span></span>  
 <span data-ttu-id="f705b-111">Metoda zwraca `S_OK` , jeśli długość strumienia pamięci można ustalić, nawet jeśli jest równa zero (0).</span><span class="sxs-lookup"><span data-stu-id="f705b-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="f705b-112">Metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC` , jeśli metoda została utworzona przy użyciu <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f705b-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f705b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f705b-113">Remarks</span></span>  
 <span data-ttu-id="f705b-114">Jeśli moduł zawiera symbole w pamięci, długość strumienia jest umieszczana w `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="f705b-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="f705b-115">Jeśli moduł nie zawiera symboli w pamięci, `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="f705b-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f705b-116">Bieżąca implementacja nie obsługuje odbicia. emisji.</span><span class="sxs-lookup"><span data-stu-id="f705b-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="f705b-117">Jeśli moduł został utworzony przy użyciu odbicia. Emituj, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="f705b-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f705b-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f705b-118">Requirements</span></span>  
 <span data-ttu-id="f705b-119">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f705b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f705b-120">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f705b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f705b-121">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f705b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f705b-122">**.NET Framework wersje:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f705b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f705b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f705b-123">See also</span></span>

- [<span data-ttu-id="f705b-124">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="f705b-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
