---
title: ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: fb8b8f3e29c141e91587a4d0cdc81cdabccdbc9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178650"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="16bc4-102">ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="16bc4-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="16bc4-103">Ustawia niezarządzany punkt przerwania przy określonym przesunięciu obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="16bc4-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16bc4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16bc4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16bc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16bc4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="16bc4-106">[w] Obiekt `CORDB_ADDRESS` określający przesunięcie obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="16bc4-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="16bc4-107">[w] Rozmiar tablicy w bajtach. `buffer`</span><span class="sxs-lookup"><span data-stu-id="16bc4-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="16bc4-108">[na zewnątrz] Tablica zawierająca opcode, który jest zastępowany przez punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="16bc4-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="16bc4-109">[na zewnątrz] Wskaźnik do liczby bajtów zwróconych w tablicy. `buffer`</span><span class="sxs-lookup"><span data-stu-id="16bc4-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16bc4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16bc4-110">Remarks</span></span>  
 <span data-ttu-id="16bc4-111">Jeśli przesunięcie obrazu macierzystego znajduje się w środowisku uruchomieniowym języka wspólnego (CLR), punkt przerwania zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="16bc4-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="16bc4-112">Dzięki temu CLR uniknąć wysyłania pozapasmowego punktu przerwania, gdy punkt przerwania jest ustawiany przez debugera.</span><span class="sxs-lookup"><span data-stu-id="16bc4-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16bc4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16bc4-113">Requirements</span></span>  
 <span data-ttu-id="16bc4-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16bc4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16bc4-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16bc4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16bc4-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16bc4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16bc4-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16bc4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
