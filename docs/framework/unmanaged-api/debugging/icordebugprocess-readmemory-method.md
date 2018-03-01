---
title: "ICorDebugProcess::ReadMemory — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d282e83fc7b7632bde850ac1341eef938d8e0dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="efe3d-102">ICorDebugProcess::ReadMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="efe3d-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="efe3d-103">Odczytuje określony obszar pamięci dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="efe3d-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe3d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="efe3d-104">Syntax</span></span>  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efe3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efe3d-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="efe3d-106">[in] A `CORDB_ADDRESS` określający adres podstawowy pamięci do odczytu.</span><span class="sxs-lookup"><span data-stu-id="efe3d-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="efe3d-107">[in] Liczba bajtów do odczytu z pamięci.</span><span class="sxs-lookup"><span data-stu-id="efe3d-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="efe3d-108">[out] Bufor, który odbiera zawartość pamięci.</span><span class="sxs-lookup"><span data-stu-id="efe3d-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="efe3d-109">[out] Wskaźnik do liczba bajtów przesłanych w buforze określona.</span><span class="sxs-lookup"><span data-stu-id="efe3d-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efe3d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efe3d-110">Remarks</span></span>  
 <span data-ttu-id="efe3d-111">`ReadMemory` Metody jest przeznaczone głównie do użycia przez debugowania międzyoperacyjnego do zbadania regiony pamięci są używane przez niezarządzane część debugowany.</span><span class="sxs-lookup"><span data-stu-id="efe3d-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="efe3d-112">Tej metody można również odczytać kodu języka pośredniego (MSIL) firmy Microsoft i kod natywny kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="efe3d-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="efe3d-113">Wszystkie punkty przerwania w zarządzanych zostaną usunięte z danych, która jest zwracana w `buffer` parametru.</span><span class="sxs-lookup"><span data-stu-id="efe3d-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="efe3d-114">Bez korekt nie były nawiązywane dla macierzystych punktów przerwania ustawionych przez [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="efe3d-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="efe3d-115">Odbywa się bez buforowania pamięci procesu.</span><span class="sxs-lookup"><span data-stu-id="efe3d-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efe3d-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efe3d-116">Requirements</span></span>  
 <span data-ttu-id="efe3d-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efe3d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efe3d-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efe3d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efe3d-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efe3d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efe3d-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efe3d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
