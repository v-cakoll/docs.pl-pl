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
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955375"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="289c8-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="289c8-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="289c8-103">[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="289c8-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="289c8-104">Odczytuje bajty z strumienia symboli w pamięci.</span><span class="sxs-lookup"><span data-stu-id="289c8-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="289c8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="289c8-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="289c8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="289c8-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="289c8-107">podczas Identyfikator modułu zawierającego strumień znajdujący się w pamięci.</span><span class="sxs-lookup"><span data-stu-id="289c8-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="289c8-108">podczas Przesunięcie w strumieniu w pamięci, od którego ma zostać rozpoczęte odczytywanie bajtów.</span><span class="sxs-lookup"><span data-stu-id="289c8-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="289c8-109">określoną Wskaźnik do buforu, do którego zostaną skopiowane dane.</span><span class="sxs-lookup"><span data-stu-id="289c8-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="289c8-110">Bufor powinien mieć `countSymbolBytes` dostępne miejsce.</span><span class="sxs-lookup"><span data-stu-id="289c8-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="289c8-111">podczas Liczba bajtów do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="289c8-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="289c8-112">określoną Gdy metoda zwraca, zawiera rzeczywistą liczbę odczytanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="289c8-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="289c8-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="289c8-113">Return Value</span></span>  
 <span data-ttu-id="289c8-114">`S_OK`, jeśli odczytano różną od zera liczbę bajtów.</span><span class="sxs-lookup"><span data-stu-id="289c8-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="289c8-115">`CORPROF_E_MODULE_IS_DYNAMIC`, jeśli moduł został utworzony przy użyciu <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="289c8-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="289c8-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="289c8-116">Remarks</span></span>  
 <span data-ttu-id="289c8-117">Metoda próbuje odczytać `countSymbolBytes` dane, zaczynając od przesunięcia `symbolsReadOffset` w strumieniu znajdującym się w pamięci. `ReadInMemorySymbols`</span><span class="sxs-lookup"><span data-stu-id="289c8-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="289c8-118">Dane są kopiowane do, `pSymbolBytes`w przypadku których oczekuje się, `countSymbolBytes` że dostępne jest miejsce.</span><span class="sxs-lookup"><span data-stu-id="289c8-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="289c8-119">`pCountSymbolsBytesRead`zawiera rzeczywistą liczbę odczytanych bajtów, która może być mniejsza `countSymbolBytes` niż Jeśli osiągnięto koniec strumienia.</span><span class="sxs-lookup"><span data-stu-id="289c8-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="289c8-120">Bieżąca implementacja nie obsługuje odbicia. emisji.</span><span class="sxs-lookup"><span data-stu-id="289c8-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="289c8-121">Jeśli moduł został utworzony przy użyciu odbicia. Emituj, metoda zwraca `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="289c8-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="289c8-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="289c8-122">Requirements</span></span>  
 <span data-ttu-id="289c8-123">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="289c8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="289c8-124">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="289c8-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="289c8-125">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="289c8-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="289c8-126">**.NET Framework wersje:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="289c8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289c8-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="289c8-127">See also</span></span>

- [<span data-ttu-id="289c8-128">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="289c8-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
