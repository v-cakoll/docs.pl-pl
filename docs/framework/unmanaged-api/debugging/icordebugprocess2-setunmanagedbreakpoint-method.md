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
ms.openlocfilehash: d4326c6d8a3ee780cf63652badc8c527f55a075c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420820"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="2fcc9-102">ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="2fcc9-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="2fcc9-103">Ustawia niezarządzanego punktu przerwania w przesunięciu określonego obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="2fcc9-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fcc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fcc9-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fcc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fcc9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2fcc9-106">[in] A `CORDB_ADDRESS` obiekt, który określa przesunięcie obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="2fcc9-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="2fcc9-107">[in] Rozmiar w bajtach z `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2fcc9-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="2fcc9-108">[out] Tablica zawiera kod operacji, która zastępuje punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="2fcc9-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="2fcc9-109">[out] Wskaźnik do liczba bajtów zwrócona w `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2fcc9-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fcc9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fcc9-110">Remarks</span></span>  
 <span data-ttu-id="2fcc9-111">W przypadku przesunięcie obrazu macierzystego w środowisko uruchomieniowe języka wspólnego (CLR), punkt przerwania zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="2fcc9-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="2fcc9-112">Dzięki temu CLR w celu uniknięcia wysyłki przerwania poza pasmem, gdy punkt przerwania jest ustawiony przez debuger.</span><span class="sxs-lookup"><span data-stu-id="2fcc9-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fcc9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2fcc9-113">Requirements</span></span>  
 <span data-ttu-id="2fcc9-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fcc9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fcc9-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fcc9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fcc9-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fcc9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fcc9-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fcc9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
