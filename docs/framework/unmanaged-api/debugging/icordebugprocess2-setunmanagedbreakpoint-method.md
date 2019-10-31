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
ms.openlocfilehash: ffab2762fd86e95c3272ca456039028e0897bc41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137177"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="3a2ed-102">ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a2ed-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="3a2ed-103">Ustawia niezarządzany punkt przerwania w określonym przesunięciu obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a2ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a2ed-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a2ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a2ed-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="3a2ed-106">podczas Obiekt `CORDB_ADDRESS`, który określa przesunięcie obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="3a2ed-107">podczas Rozmiar (w bajtach) tablicy `buffer`.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="3a2ed-108">określoną Tablica zawierająca kod operacji, który jest zastępowany przez punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="3a2ed-109">określoną Wskaźnik do liczby bajtów zwróconych w tablicy `buffer`.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a2ed-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a2ed-110">Remarks</span></span>  
 <span data-ttu-id="3a2ed-111">Jeśli przesunięcie obrazu natywnego znajduje się w środowisku uruchomieniowym języka wspólnego (CLR), punkt przerwania zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="3a2ed-112">Pozwala to na uniknięcie wysyłania przez środowisko uruchomieniowe punktu przerwania poza pasmem, gdy punkt przerwania jest ustawiony przez debuger.</span><span class="sxs-lookup"><span data-stu-id="3a2ed-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a2ed-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a2ed-113">Requirements</span></span>  
 <span data-ttu-id="3a2ed-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a2ed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a2ed-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a2ed-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a2ed-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a2ed-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a2ed-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a2ed-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
