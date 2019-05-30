---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3df5324e23ebeded38f3aa9843f81701f7fd333
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251046"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="e0a22-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="e0a22-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="e0a22-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="e0a22-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="e0a22-104">Odczytuje bajtów ze strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e0a22-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0a22-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0a22-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0a22-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0a22-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="e0a22-107">[in] Identyfikator modułu, zawierająca strumień w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e0a22-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="e0a22-108">[in] Przesunięcie w strumieniu w pamięci, w którym ma zostać rozpoczęte odczytywanie bajtów.</span><span class="sxs-lookup"><span data-stu-id="e0a22-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="e0a22-109">[out] Wskaźnik do buforu, do którego zostaną skopiowane dane.</span><span class="sxs-lookup"><span data-stu-id="e0a22-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="e0a22-110">Rozmiar buforu powinien mieć `countSymbolBytes` dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="e0a22-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="e0a22-111">[in] Liczba bajtów do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="e0a22-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="e0a22-112">[out] Gdy metoda zwróci wartość, zawiera rzeczywista liczba odczytanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="e0a22-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0a22-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0a22-113">Return Value</span></span>  
 <span data-ttu-id="e0a22-114">`S_OK`, jeśli zostały wczytane niezerową liczbę bajtów.</span><span class="sxs-lookup"><span data-stu-id="e0a22-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="e0a22-115">`CORPROF_E_MODULE_IS_DYNAMIC`, jeśli moduł został utworzony przy użyciu <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="e0a22-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0a22-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0a22-116">Remarks</span></span>  
 <span data-ttu-id="e0a22-117">`ReadInMemorySymbols` Metoda podejmuje próbę odczytu `countSymbolBytes` danych, rozpoczynając od przesunięcia `symbolsReadOffset` w strumieniu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e0a22-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="e0a22-118">Dane są kopiowane do `pSymbolBytes`, które powinny mieć `countSymbolBytes` dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="e0a22-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="e0a22-119">`pCountSymbolsBytesRead` zawiera rzeczywista liczba bajtów odczytanych, który może być mniejsza niż `countSymbolBytes` Jeśli osiągnięty zostanie koniec strumienia.</span><span class="sxs-lookup"><span data-stu-id="e0a22-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0a22-120">Bieżąca implementacja nie obsługuje Reflection.Emit.</span><span class="sxs-lookup"><span data-stu-id="e0a22-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="e0a22-121">Jeśli moduł został utworzony przy użyciu Reflection.Emit, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="e0a22-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0a22-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0a22-122">Requirements</span></span>  
 <span data-ttu-id="e0a22-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0a22-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a22-124">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e0a22-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0a22-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0a22-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0a22-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0a22-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a22-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0a22-127">See also</span></span>

- [<span data-ttu-id="e0a22-128">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0a22-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
