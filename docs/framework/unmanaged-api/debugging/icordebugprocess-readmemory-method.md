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
ms.openlocfilehash: ef9e339c74b2d2785d758ed9c4adfc1901073253
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139360"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="f20c5-102">ICorDebugProcess::ReadMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="f20c5-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="f20c5-103">Odczytuje określony obszar pamięci dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="f20c5-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f20c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f20c5-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f20c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f20c5-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="f20c5-106">podczas Wartość `CORDB_ADDRESS`, która określa podstawowy adres pamięci, która ma zostać odczytana.</span><span class="sxs-lookup"><span data-stu-id="f20c5-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="f20c5-107">podczas Liczba bajtów do odczytu z pamięci.</span><span class="sxs-lookup"><span data-stu-id="f20c5-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="f20c5-108">określoną Bufor, który odbiera zawartość pamięci.</span><span class="sxs-lookup"><span data-stu-id="f20c5-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="f20c5-109">określoną Wskaźnik do liczby bajtów transferowanych do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="f20c5-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f20c5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f20c5-110">Remarks</span></span>  
 <span data-ttu-id="f20c5-111">Metoda `ReadMemory` jest przeznaczona głównie do użycia przez debugowanie międzyoperacyjną do inspekcji regionów pamięci, które są używane przez niezarządzaną część debugowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f20c5-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="f20c5-112">Ta metoda może być również używana do odczytywania kodu języka pośredniego firmy Microsoft (MSIL) i natywnego kodu skompilowanego JIT.</span><span class="sxs-lookup"><span data-stu-id="f20c5-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="f20c5-113">Wszystkie zarządzane punkty przerwania zostaną usunięte z danych, które są zwracane w parametrze `buffer`.</span><span class="sxs-lookup"><span data-stu-id="f20c5-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="f20c5-114">Nie będą wprowadzane żadne korekty dla natywnych punktów przerwania ustawionych przez [ICorDebugProcess2:: SetUnmanagedBreakpoint —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="f20c5-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="f20c5-115">Nie jest wykonywane buforowanie pamięci procesu.</span><span class="sxs-lookup"><span data-stu-id="f20c5-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f20c5-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f20c5-116">Requirements</span></span>  
 <span data-ttu-id="f20c5-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f20c5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f20c5-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f20c5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f20c5-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f20c5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f20c5-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f20c5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
