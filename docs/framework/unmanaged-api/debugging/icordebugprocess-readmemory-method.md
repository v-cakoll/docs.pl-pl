---
title: ICorDebugProcess::ReadMemory — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 218279684304b766a9bf009f5891ac4910254a3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994386"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="62105-102">ICorDebugProcess::ReadMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="62105-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="62105-103">Odczytuje określony obszar pamięci dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="62105-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62105-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62105-104">Syntax</span></span>  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62105-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62105-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="62105-106">[in] A `CORDB_ADDRESS` wartość, która określa adres bazowy pamięci do odczytu.</span><span class="sxs-lookup"><span data-stu-id="62105-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="62105-107">[in] Liczba bajtów, które mają zostać odczytana z pamięci.</span><span class="sxs-lookup"><span data-stu-id="62105-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="62105-108">[out] Bufor, który odbiera zawartość pamięci.</span><span class="sxs-lookup"><span data-stu-id="62105-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="62105-109">[out] Wskaźnik do liczby bajtów przesłanych do określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="62105-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62105-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62105-110">Remarks</span></span>  
 <span data-ttu-id="62105-111">`ReadMemory` Metoda jest przeznaczona głównie do użycia przez debugowania międzyoperacyjnego, aby sprawdzić regiony pamięci, które są używane przez niezarządzane część debugowany program.</span><span class="sxs-lookup"><span data-stu-id="62105-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="62105-112">Tę metodę można również odczytywać kod intermediate language (MSIL) firmy Microsoft i natywnego kodu kompilowanego dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="62105-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="62105-113">Wszelkie zarządzane punkty przerwania zostaną usunięte z danych, które są zwracane w `buffer` parametru.</span><span class="sxs-lookup"><span data-stu-id="62105-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="62105-114">Nie zmiany zostaną wprowadzone dla natywnych punkty przerwania ustawione [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="62105-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="62105-115">Brak buforowania pamięci procesu jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="62105-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62105-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62105-116">Requirements</span></span>  
 <span data-ttu-id="62105-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62105-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62105-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62105-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62105-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62105-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62105-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62105-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
