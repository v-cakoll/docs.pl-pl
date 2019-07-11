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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f16a5d1bad80a5aad8573508aab5fbf98c8c2a03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736840"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="996cb-102">ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="996cb-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="996cb-103">Ustawia niezarządzany punkt przerwania w przesunięciu określonego obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="996cb-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="996cb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="996cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="996cb-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="996cb-106">[in] A `CORDB_ADDRESS` obiekt, który określa przesunięcie obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="996cb-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="996cb-107">[in] Rozmiar w bajtach z `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="996cb-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="996cb-108">[out] Tablica, która zawiera kod operacji, który jest zastępowany przez punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="996cb-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="996cb-109">[out] Wskaźnik do liczby bajtów zwróconych w `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="996cb-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="996cb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="996cb-110">Remarks</span></span>  
 <span data-ttu-id="996cb-111">Jeśli przesunięcie obrazów natywnych w środowisko uruchomieniowe języka wspólnego (CLR), punkt przerwania zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="996cb-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="996cb-112">Dzięki temu środowisko CLR uniknąć przerwania out-of-band wysyłki, gdy punkt przerwania jest ustawiony przez debuger.</span><span class="sxs-lookup"><span data-stu-id="996cb-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996cb-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="996cb-113">Requirements</span></span>  
 <span data-ttu-id="996cb-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="996cb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="996cb-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="996cb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="996cb-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="996cb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="996cb-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="996cb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
