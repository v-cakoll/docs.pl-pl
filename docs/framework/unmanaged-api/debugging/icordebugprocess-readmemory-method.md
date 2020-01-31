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
ms.openlocfilehash: dca2a4e5ee869346108137a8ba01ab8855756725
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792558"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="13ce6-102">ICorDebugProcess::ReadMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="13ce6-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="13ce6-103">Odczytuje określony obszar pamięci dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="13ce6-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13ce6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13ce6-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13ce6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13ce6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="13ce6-106">podczas Wartość `CORDB_ADDRESS`, która określa podstawowy adres pamięci, która ma zostać odczytana.</span><span class="sxs-lookup"><span data-stu-id="13ce6-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="13ce6-107">podczas Liczba bajtów do odczytu z pamięci.</span><span class="sxs-lookup"><span data-stu-id="13ce6-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="13ce6-108">określoną Bufor, który odbiera zawartość pamięci.</span><span class="sxs-lookup"><span data-stu-id="13ce6-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="13ce6-109">określoną Wskaźnik do liczby bajtów transferowanych do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="13ce6-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13ce6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13ce6-110">Remarks</span></span>  
 <span data-ttu-id="13ce6-111">Metoda `ReadMemory` jest przeznaczona głównie do użycia przez debugowanie międzyoperacyjną do inspekcji regionów pamięci, które są używane przez niezarządzaną część debugowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="13ce6-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="13ce6-112">Ta metoda może być również używana do odczytywania kodu języka pośredniego firmy Microsoft (MSIL) i natywnego kodu skompilowanego JIT.</span><span class="sxs-lookup"><span data-stu-id="13ce6-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="13ce6-113">Wszystkie zarządzane punkty przerwania zostaną usunięte z danych, które są zwracane w parametrze `buffer`.</span><span class="sxs-lookup"><span data-stu-id="13ce6-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="13ce6-114">Nie będą wprowadzane żadne korekty dla natywnych punktów przerwania ustawionych przez [ICorDebugProcess2:: SetUnmanagedBreakpoint —](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="13ce6-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="13ce6-115">Nie jest wykonywane buforowanie pamięci procesu.</span><span class="sxs-lookup"><span data-stu-id="13ce6-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13ce6-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13ce6-116">Requirements</span></span>  
 <span data-ttu-id="13ce6-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13ce6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13ce6-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="13ce6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13ce6-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="13ce6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13ce6-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13ce6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
