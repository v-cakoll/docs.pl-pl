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
ms.openlocfilehash: af90886390b59932d3ae146a70fc2901ec1c378d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894669"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="fb644-102">ICorDebugBreakpointEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb644-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="fb644-103">Pobiera określoną liczbę wystąpień ICorDebugBreakpoint z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="fb644-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb644-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb644-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb644-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb644-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="fb644-106">podczas Liczba `ICorDebugBreakpoint` wystąpień do pobrania.</span><span class="sxs-lookup"><span data-stu-id="fb644-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="fb644-107">określoną Tablica wskaźników, z których każdy wskazuje `ICorDebugBreakpoint` obiekt, który reprezentuje punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="fb644-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="fb644-108">określoną Wskaźnik do liczby faktycznie zwróconych `ICorDebugBreakpoint` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="fb644-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="fb644-109">Ta wartość może być równa `celt` null, jeśli jest taka.</span><span class="sxs-lookup"><span data-stu-id="fb644-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb644-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb644-110">Requirements</span></span>  
 <span data-ttu-id="fb644-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb644-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb644-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb644-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb644-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fb644-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb644-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb644-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
