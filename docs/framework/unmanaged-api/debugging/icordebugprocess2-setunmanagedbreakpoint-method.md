---
title: "ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.SetUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd2d6ac2967b4314a57aa30bbb34ff3d354a6365
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="ba996-102">ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="ba996-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="ba996-103">Ustawia niezarządzanego punktu przerwania w przesunięciu określonego obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="ba996-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba996-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba996-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba996-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba996-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ba996-106">[in] A `CORDB_ADDRESS` obiekt, który określa przesunięcie obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="ba996-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="ba996-107">[in] Rozmiar w bajtach z `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ba996-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="ba996-108">[out] Tablica zawiera kod operacji, która zastępuje punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="ba996-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="ba996-109">[out] Wskaźnik do liczba bajtów zwrócona w `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ba996-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba996-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba996-110">Remarks</span></span>  
 <span data-ttu-id="ba996-111">W przypadku przesunięcie obrazu macierzystego w środowisko uruchomieniowe języka wspólnego (CLR), punkt przerwania zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="ba996-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="ba996-112">Dzięki temu CLR w celu uniknięcia wysyłki przerwania poza pasmem, gdy punkt przerwania jest ustawiony przez debuger.</span><span class="sxs-lookup"><span data-stu-id="ba996-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba996-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba996-113">Requirements</span></span>  
 <span data-ttu-id="ba996-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba996-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba996-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba996-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba996-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba996-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba996-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba996-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
