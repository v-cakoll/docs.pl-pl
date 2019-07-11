---
title: ICorDebugBreakpointEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87249dae0eff4ea4899a63c0d13e79c266df453a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745005"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="302b3-102">ICorDebugBreakpointEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="302b3-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="302b3-103">Pobiera określoną liczbę wystąpień ICorDebugBreakpoint z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="302b3-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="302b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="302b3-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="302b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="302b3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="302b3-106">[in] Liczba `ICorDebugBreakpoint` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="302b3-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="302b3-107">[out] Tablica wskaźników, z których każdy wskazuje `ICorDebugBreakpoint` obiekt, który reprezentuje punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="302b3-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="302b3-108">[out] Wskaźnik do liczby `ICorDebugBreakpoint` wystąpień rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="302b3-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="302b3-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="302b3-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="302b3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="302b3-110">Requirements</span></span>  
 <span data-ttu-id="302b3-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="302b3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="302b3-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="302b3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="302b3-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="302b3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="302b3-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="302b3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
